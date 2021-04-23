# 1. superset介绍

>Superset是一款开源的现代化企业级BI。它是目前开源的数据分析和可视化工具中比较好用的，功能简单但可以满足我们对数据的基本需求，支持多种数据源，图表类型多，易维护，易进行二次开发。

# 2. 特点

1. 丰富数据可视化集
2. 易于使用的界面,用于浏览器可视化数据
3. 创建共享仪表盘
4. 可提供身份验证

# 3.支持的数据库

> superset几乎支持所有日常所用的数据库

![1619162035389](E:\superSet\typora-user-images\1619162035389.png)

# 4.Superset的安装

~~~sh
1、首先去Anaconda官网下载安装脚本
Anaconda3-2019.07-Linux-x86_64.sh

2、上传Anaconda3-2019.07-Linux-x86_64.sh
将Anaconda3-2019.07-Linux-x86_64.sh上传到/opt/server
3、运行Anaconda3-2019.07-Linux-x86_64.sh脚本
sh Anaconda3-2019.07-Linux-x86_64.sh
安装过程输入：一路回车、yes
4、配置环境变量
vim /etc/profile
#Anaconda 
export PATH=$PATH:/root/anaconda3/bin
然后执行source命令让配置生效
source /etc/profile
然后vim /root/.bashrc文件, 添加以下内容,否则终端会出现base字样
conda deactivate
5、验证是否安装python3成功
在终端中输入:python3
安装Superset
pip3 install cryptography
pip3 install --upgrade setuptools pip
yum upgrade python-setuptools
yum install gcc gcc-c++ libffi-devel python-devel python-pip python-wheel openssl-devel libsasl2-devel openldap-devel
pip  install superset==0.30.0 -i https://pypi.douban.com/simple


pip install email_validator

3、创建管理员用户名和密码
fabmanager create-admin --app superset
邮箱回车
用户名等都是admin
4、初始化superset
superset db upgrade
5、创建默认角色和权限
superset init
6、安装相关配套软件
yum install python-devel -y
yum install mysql-devel -y
pip install mysqlclient

7、启动superset
打开浏览器，输入以下地址来访问Superset主页面
superset run -h 主机IP -p 8080 --with-threads --reload --debugger
 
7、登录superset
http://192.168.88.160:8080/superset/welcome
用户名： admin
密码：123456
~~~

# 5. Superset以中文的方式登录

![1619162340327](E:\superSet\typora-user-images\1619162340327.png)

# 6.superset入门案例

这里是测试就先造张表

~~~SQL

CREATE DATABASE /*!32312 IF NOT EXISTS*/`superset_demo` /*!40100 DEFAULT CHARACTER SET utf8 */;

USE `superset_demo`;

/*Table structure for table `dm_sales` */

DROP TABLE IF EXISTS `dm_sales`;

CREATE TABLE `dm_sales` (
  `id` longtext,
  `date1` longtext,
  `channelid` longtext,
  `productid` longtext,
  `regionid` longtext,
  `amount` int(11) DEFAULT NULL,
  `price` double DEFAULT NULL,
  `channelname` longtext,
  `productname` longtext,
  `regionname` longtext
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

/*Data for the table `dm_sales` */

insert  into `dm_sales`(`id`,`date1`,`channelid`,`productid`,`regionid`,`amount`,`price`,`channelname`,`productname`,`regionname`) values ('0001','2019-02-01','01','01','010',1,3400,'商场','meta20','北京'),('0002','2019-02-01','02','02','021',2,6800,'京东','p30','上海'),('0003','2019-02-01','01','01','010',1,3400,'商场','meta20','北京'),('0004','2019-02-01','01','02','021',1,3400,'商场','p30','上海'),('0005','2019-02-01','02','01','010',1,3400,'京东','meta20','北京'),('0006','2019-02-01','01','01','021',2,6800,'商场','meta20','上海'),('0007','2019-02-01','03','02','010',1,3400,'天猫','p30','北京'),('0008','2019-02-01','01','01','021',1,3400,'商场','meta20','上海'),('0009','2019-02-01','01','03','010',1,3400,'商场','ihpone Xs','北京'),('0010','2019-02-01','02','01','021',3,10200,'京东','meta20','上海'),('0011','2019-02-01','01','04','010',1,3400,'商场','小米 9','北京'),('0012','2019-02-01','03','01','021',1,3400,'天猫','meta20','上海'),('0013','2019-02-01','01','04','010',1,3400,'商场','小米 9','北京'),('0014','2019-02-02','01','01','010',1,3400,'商场','meta20','北京'),('0015','2019-02-02','02','02','021',2,6800,'京东','p30','上海'),('0016','2019-02-02','01','01','010',1,3400,'商场','meta20','北京'),('0017','2019-02-02','01','02','021',1,3400,'商场','p30','上海'),('0018','2019-02-02','02','01','010',1,3400,'京东','meta20','北京'),('0019','2019-02-02','01','01','021',2,6800,'商场','meta20','上海'),('0020','2019-02-02','03','02','010',1,3400,'天猫','p30','北京'),('0021','2019-02-02','01','01','021',1,3400,'商场','meta20','上海'),('0022','2019-02-02','01','03','010',1,3400,'商场','ihpone Xs','北京'),('0023','2019-02-02','02','01','021',3,10200,'京东','meta20','上海'),('0024','2019-02-02','01','04','010',1,3400,'商场','小米 9','北京'),('0025','2019-02-02','03','01','021',1,3400,'天猫','meta20','上海'),('0026','2019-02-02','01','04','010',1,3400,'商场','小米 9','北京'),('0001','2019-02-01','01','01','010',1,3400,'商场','meta20','北京'),('0002','2019-02-01','02','02','021',2,6800,'京东','p30','上海'),('0003','2019-02-01','01','01','010',1,3400,'商场','meta20','北京'),('0004','2019-02-01','01','02','021',1,3400,'商场','p30','上海'),('0005','2019-02-01','02','01','010',1,3400,'京东','meta20','北京'),('0006','2019-02-01','01','01','021',2,6800,'商场','meta20','上海'),('0007','2019-02-01','03','02','010',1,3400,'天猫','p30','北京'),('0008','2019-02-01','01','01','021',1,3400,'商场','meta20','上海'),('0009','2019-02-01','01','03','010',1,3400,'商场','ihpone Xs','北京'),('0010','2019-02-01','02','01','021',3,10200,'京东','meta20','上海'),('0011','2019-02-01','01','04','010',1,3400,'商场','小米 9','北京'),('0012','2019-02-01','03','01','021',1,3400,'天猫','meta20','上海'),('0013','2019-02-01','01','04','010',1,3400,'商场','小米 9','北京'),('0014','2019-02-02','01','01','010',1,3400,'商场','meta20','北京'),('0015','2019-02-02','02','02','021',2,6800,'京东','p30','上海'),('0016','2019-02-02','01','01','010',1,3400,'商场','meta20','北京'),('0017','2019-02-02','01','02','021',1,3400,'商场','p30','上海'),('0018','2019-02-02','02','01','010',1,3400,'京东','meta20','北京'),('0019','2019-02-02','01','01','021',2,6800,'商场','meta20','上海'),('0020','2019-02-02','03','02','010',1,3400,'天猫','p30','北京'),('0021','2019-02-02','01','01','021',1,3400,'商场','meta20','上海'),('0022','2019-02-02','01','03','010',1,3400,'商场','ihpone Xs','北京'),('0023','2019-02-02','02','01','021',3,10200,'京东','meta20','上海'),('0024','2019-02-02','01','04','010',1,3400,'商场','小米 9','北京'),('0025','2019-02-02','03','01','021',1,3400,'天猫','meta20','上海'),('0026','2019-02-02','01','04','010',1,3400,'商场','小米 9','北京'),('0001','2019-02-01','01','01','010',1,3400,'商场','meta20','北京'),('0002','2019-02-01','02','02','021',2,6800,'京东','p30','上海'),('0003','2019-02-01','01','01','010',1,3400,'商场','meta20','北京'),('0004','2019-02-01','01','02','021',1,3400,'商场','p30','上海'),('0005','2019-02-01','02','01','010',1,3400,'京东','meta20','北京'),('0006','2019-02-01','01','01','021',2,6800,'商场','meta20','上海'),('0007','2019-02-01','03','02','010',1,3400,'天猫','p30','北京'),('0008','2019-02-01','01','01','021',1,3400,'商场','meta20','上海'),('0009','2019-02-01','01','03','010',1,3400,'商场','ihpone Xs','北京'),('0010','2019-02-01','02','01','021',3,10200,'京东','meta20','上海'),('0011','2019-02-01','01','04','010',1,3400,'商场','小米 9','北京'),('0012','2019-02-01','03','01','021',1,3400,'天猫','meta20','上海'),('0013','2019-02-01','01','04','010',1,3400,'商场','小米 9','北京'),('0014','2019-02-02','01','01','010',1,3400,'商场','meta20','郑州'),('0015','2019-02-02','02','02','021',2,6800,'京东','p30','上海'),('0016','2019-02-02','01','01','010',1,3400,'商场','meta20','北京'),('0017','2019-02-02','01','02','021',1,3400,'商场','p30','上海'),('0018','2019-02-02','02','01','010',1,3400,'京东','meta20','北京'),('0019','2019-02-02','01','01','021',2,6800,'商场','meta20','上海'),('0020','2019-02-02','03','02','010',1,3400,'天猫','p30','北京'),('0021','2019-02-02','01','01','021',1,3400,'商场','meta20','上海'),('0022','2019-02-02','01','03','010',1,3400,'商场','ihpone Xs','北京'),('0023','2019-02-02','02','01','021',3,10200,'京东','meta20','上海'),('0024','2019-02-02','01','04','010',1,3400,'商场','小米 9','北京'),('0025','2019-02-02','03','01','021',1,3400,'天猫','meta20','上海'),('0026','2019-02-02','01','04','010',1,3400,'商场','小米 9','北京'),('0027','2019-02-03','01','04','010',1,61400,'商场','小米 9','北京'),('0028','2019-02-04','02','04','010',1,68400,'商场','小米 9','北京'),('0028','2019-02-05','03','04','010',1,71400,'商场','小米 9','杭州'),('0029','2019-02-06','01','04','010',1,81400,'商场','小米 9','上海'),('0030','2019-02-07','02','04','010',1,93410,'商场','小米 9','深圳'),('0031','2019-02-08','02','04','010',1,113410,'商场','小米 9','深圳'),('0032','2019-02-09','01','04','010',1,53410,'商场','小米 9','沭阳'),('0033','2019-02-10','01','04','010',1,53410,'商场','小米 9','南通');

/*Table structure for table `t_user` */

DROP TABLE IF EXISTS `t_user`;

CREATE TABLE `t_user` (
  `id` tinytext,
  `name` tinytext,
  `age` int(11) DEFAULT NULL,
  `gender` int(11) DEFAULT NULL,
  `province` tinytext,
  `city` tinytext,
  `region` tinytext,
  `phone` tinytext,
  `birthday` tinytext,
  `hobby` tinytext,
  `register_date` tinytext
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

/*Data for the table `t_user` */

insert  into `t_user`(`id`,`name`,`age`,`gender`,`province`,`city`,`region`,`phone`,`birthday`,`hobby`,`register_date`) values ('392456197008193000','张三',20,0,'北京市','昌平区','回龙观','18589407692','1970-08-19','美食;篮球;足球','2018-08-06 09:44:43'),('267456198006210000','李四',25,1,'河南省','郑州市','郑东新区','18681109672','1980-06-21','音乐;阅读;旅游','2017-04-07 09:14:13'),('892456199007203000','王五',24,1,'湖北省','武汉市','汉阳区','18798009102','1990-07-20','写代码;读代码;算法','2016-06-08 07:34:23'),('492456198712198000','赵六',26,2,'陕西省','西安市','莲湖区','18189189195','1987-12-19','购物;旅游','2016-01-09 19:15:53');

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

~~~

## 6.1添加新数据库

![1619162832734](E:\superSet\typora-user-images\1619162832734.png)

![1619162964954](E:\superSet\typora-user-images\1619162964954.png)

> mysql的url地址：mysql://root:123456@node1/superset_demo?charset=utf8

![1619163128751](E:\superSet\typora-user-images\1619163128751.png)

## 6.2 编写Sql

![1619163296895](E:\superSet\typora-user-images\1619163296895.png)

![1619163426414](E:\superSet\typora-user-images\1619163426414.png)

![1619163660752](E:\superSet\typora-user-images\1619163660752.png)

sql语句

~~~sql
select
 case when gender = 0 then '男'
     when gender = 1 then '女'
  else '保密'
    end as gender,
 count(id) as total_cnt
from
 t_user
group by gender
~~~



![1619163778114](E:\superSet\typora-user-images\1619163778114.png)

![1619163829618](E:\superSet\typora-user-images\1619163829618.png)

![1619163870086](E:\superSet\typora-user-images\1619164156069.png)

![1619165903599](E:\superSet\typora-user-images\1619165903599.png)

![1619166090129](E:\superSet\typora-user-images\1619166090129.png)

### 1 以柱状图的方式显示

![1619166127311](E:\superSet\typora-user-images\1619166127311.png)

# 7.Superset数据可视化实战

### 2 趋势图

![1619166470432](E:\superSet\typora-user-images\1619166470432.png)

![1619166493810](E:\superSet\typora-user-images\1619166493810.png)

~~~sql
select date1,
       channelname,
       sum(price) total_price
from dm_sales
group by date1,
         channelname;
~~~

![1619166588242](E:\superSet\typora-user-images\1619166588242.png)

![1619166715860](E:\superSet\typora-user-images\1619166715860.png)

![1619166747764](E:\superSet\typora-user-images\1619166747764.png)

![1619166772404](E:\superSet\typora-user-images\1619166772404.png)

![1619166799333](E:\superSet\typora-user-images\1619166799333.png)

![1619166835766](E:\superSet\typora-user-images\1619166835766.png)

![1619167060986](E:\superSet\typora-user-images\1619167060986.png)

![1619167088201](E:\superSet\typora-user-images\1619167088201.png)

### 3 根据日期、渠道统计订单总额（双环图）

![1619168154941](E:\superSet\typora-user-images\1619168154941.png)

![1619168890422](E:\superSet\typora-user-images\1619168890422.png)

~~~sql
show databases;
use superset_demo;

select date1,
       channelname
from dm_sales
group by date1,
         channelname;
~~~



![1619168931156](E:\superSet\typora-user-images\1619168931156.png)

![1619168961612](E:\superSet\typora-user-images\1619168961612.png)

![1619169002078](E:\superSet\typora-user-images\1619169002078.png)

###### ![619176706386](E:\superSet\typora-user-images\1619176706386.png)



![1619177404707](E:\superSet\typora-user-images\1619177404707.png)

### 4 根据日期、区域、渠道、产品统计订单总额（层级环图）

![1619177782750](E:\superSet\typora-user-images\1619177782750.png)



![1619177817223](E:\superSet\typora-user-images\1619177817223.png)

![1619178226893](E:\superSet\typora-user-images\1619178226893.png)

![1619178292430](E:\superSet\typora-user-images\1619178292430.png)

![1619178206522](E:\superSet\typora-user-images\1619178206522.png)

![1619178324207](E:\superSet\typora-user-images\1619178324207.png)

### 5 根据日期、区域统计订单总额（数据透视表)

![1619179083406](E:\superSet\typora-user-images\1619179083406.png)

![1619179127284](E:\superSet\typora-user-images\1619179127284.png)

~~~sql
select
 str_to_date(date1,'%Y-%m-%d') date1,
 regionname,
 sum(amount) as total_amount,
 sum(price) as total_price
from
 dm_sales
group by
 date1,
 regionname
~~~

![1619179209095](E:\superSet\typora-user-images\1619179209095.png)



![1619179234602](E:\superSet\typora-user-images\1619179234602.png)

![1619179432248](E:\superSet\typora-user-images\1619179432248.png)

![1619179448622](E:\superSet\typora-user-images\1619179448622.png)

# 8 Superset Dashboards看板展示实战

![1619179750933](E:\superSet\typora-user-images\1619179750933.png)

![1619179809437](E:\superSet\typora-user-images\1619179809437.png)

![1619179841988](E:\superSet\typora-user-images\1619179841988.png)

![1619179901669](E:\superSet\typora-user-images\1619179901669.png)

![1619179962251](E:\superSet\typora-user-images\1619179962251.png)

![1619179999829](E:\superSet\typora-user-images\1619179999829.png)

将你之前的图表拖到看板合适的位置,并调整大小

![1619180153593](E:\superSet\typora-user-images\1619180153593.png)

然后进行保存

![1619180173505](E:\superSet\typora-user-images\1619180173505.png)

效果:

![1619180218262](E:\superSet\typora-user-images\1619180218262.png)