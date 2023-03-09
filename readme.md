# 自学谷粒商城项目

一.项目环境的搭建

1.采用逆向工程，在github上创建一个项目，然后通过idea->file->new->remote克隆项目下来。

![image-20230308174521175](C:\Users\wenshuai\AppData\Roaming\Typora\typora-user-images\image-20230308174521175.png)

在主项目下，new对应的新的模块，如果是springboot， 就选择spring initializer，注意要选择maven。

![image-20230308174709205](C:\Users\wenshuai\AppData\Roaming\Typora\typora-user-images\image-20230308174709205.png)

2.从子模块中随便选择一个pom复制到主工程下，或者创建一个也行。这pom只作为聚合功能，执行maven install时并不打包成jar\war，所以packing一定要位pom。并且记得换groupid和artifactid。在编写models标签，最后将这个pom文件添加到maven中，刷新即可。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.atguigu.mall</groupId>
    <artifactId>mall</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>mall</name>
    <description>聚合服务</description>

<!--    父pom的packing必须为pom，表示在install时不会生成jar、war包，该pom文件只能作为整合-->
    <packaging>pom</packaging>


<!--    将各个模块聚合起来，编译顺序也如下，所以这是使用父pom文件的好处 -->
    <modules>
        <module>mall-coupon</module>
        <module>mall-member</module>
        <module>mall-order</module>
        <module>mall-product</module>
        <module>mall-ware</module>
    </modules>
</project>
```

![image-20230308175049553](C:\Users\wenshuai\AppData\Roaming\Typora\typora-user-images\image-20230308175049553.png)