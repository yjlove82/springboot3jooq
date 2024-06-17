# Springboot3 - JOOQ Project
## 개발환경
- springboot 3.3
- jdk17
- maven
- mariadb 11.4.2 (docker container)

## DB Setting
### DB 설치
```shell
docker run --name mariadb -d -p 3306:3306 --restart=always -e MARIADB_ALLOW_EMPTY_ROOT_PASSWORD=true mariadb
docker exec -it mariadb bash

mariadb -u root
```
### database / account 생성
```sql
create database yjlove82;
create user 'yjlove82'@'%' identified by 'love1234';
grant all privileges on yjlove82.* to 'yjlove82'@'%' identified BY 'love1234';
flush privileges;
```

### table 생성
```sql
create table admin(
    number            int unsigned auto_increment,
    id                varchar(20)          default ''                    not null,
    pass              varchar(40)          default ''                    not null,
    name              varchar(20)          default ''                    not null,
    phone             varchar(32)          default ''                    not null,
    email             varchar(32)          default ''                    not null,
    date              timestamp            default now() not null,
    primary key (number)
);

create table admin_ip(
    admin_id          varchar(20)  not null,
    ip                varchar(20)  not null,
    etc               varchar(200) null,
    primary key (admin_id, ip)
);
```

