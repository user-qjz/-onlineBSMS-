# 配置使用文档

## 项目环境

1. mysql 8.0.35

2. apache-tomcat-9.0.83

3. java 8


## 数据库相关配置

1. 使用utf8mb4字符集

2. 创建数据库dbsc_lab3，用户dbsc_lab3，用户密码设为dbsc

3. ```sql
   grant all on dbsc_lab3.* to dbsc_lab3;
   ```

4. 选择数据库dbsc_lab3（`use dbsc_lab3;`），依次运行脚本文件onlineBS_schema.sql、onlineBS_data.sql

## 源代码编译

1. 使用IDEA2023.3.1专业版打开项目
2. Project Structure ->Project中选择jdk1.8 
3. Project Structure -> Facets中Add->web
4. Project Structure -> Artifacts -> Web Application: Exploded -> from Modules，选择相应模块即可
5. Run-> Edit Configurations
   1. Tomcat Server->Local
   2. Application server->configure，选择tomcat安装路径
   3.  Deployment -> + -> Artifact

## 项目运行

### 1.用源代码直接运行

​		编译结束后点击IDEA内的运行按钮直接运行

### 2.使用二进制打包文件运行

1. 将打包的项目文件jspservlet.war放置于tomcat的webapps文件夹下
2. 运行tomcat
3. 访问http://localhost:8080/jspservlet/

> 注：上述两种运行方式都需要预先配置好数据库，但使用二进制打包文件运行不需要预先编译

# 源代码文件说明

## 数据库部分

D:.

  book_data.csv（导出的统计表）

  generate.py（构造数据）

  generate_pw.py（构造数据）

  hash_pw.py（构造数据）

  onlineBS_data.sql（导入数据）

  onlineBS_drop.sql（删除模式）

  onlineBS_schema.sql（创建模式）

  pw.csv（存储普通用户的明文密码）



## 前端代码部分

web

│ account.jsp（普通用户账户管理界面）

│ add_admin.jsp（添加管理员用户界面）

│ add_book.jsp（添加书籍界面）

│ admins.jsp（展示管理员用户界面）

│ admin_account.jsp（管理员账户管理界面）

│ admin_sidebar.jsp（管理员界面侧边栏）

│ author_detail.jsp（作者详情界面）

│ books.jsp（书籍管理界面）

│ book_detail.jsp（书目详情页面）

│ change_account_info.jsp（修改账户信息界面）

│ change_account_passwd.jsp（修改账户密码界面）

│ current_order.jsp（当前订单展示界面）

│ customers.jsp（普通用户管理界面）

│ history_order.jsp（历史订单展示界面）

│ home.jsp（普通用户书籍展示界面）

│ index.jsp（默认主界面）

│ login.jsp（登录界面）

│ press_detail.jsp（出版商详情页面）

│ register.jsp（注册界面）

│ sidebar.jsp（普通用户侧边栏界面）

│ 

├─assets

│ ├─css            //bootstrap5的css文件

│ ├─img

│ │   backimg.jpg       //登录界面的背景图片

│ │   web_icon.svg       //网站图标

│ │   

│ ├─js            //bootstrap5的js文件

│ ├─self_css           // 自己编写的部分css文件

│ │   self_content.css

│ │   self_sidebar.css

│ │   self_table.css

│ │   

│ └─self_js         //自己编写的部分文件

│     delete_cookies.jsp

│     verify_cookies.js

│     

└─WEB-INF

  │ web.xml

  │ 

  └─lib

​      jstl.jar

​      mysql-connector-j-8.0.32.jar

​      standard.jar



## 后端代码部分

src

│ 

└─com

  └─jspservlet

​    ├─dao           //数据库交互相关

​    │   AdminDao.java（管理员的数据库操作）

​    │   BookControl.java（对书籍的所有操作）

​    │   BoughtBookControl.java（对已购买书籍的操作）

​    │   CustomerDao.java（普通用户的数据库操作）

​    │   HistoricalControl.java（历史订单的操作）

​    │   ManageAccount.java（账户管理操作）

​    │   OrderControl.java（对订单的操作）

​    │   UserDao.java（AdminDao.java和CustomerDao.java的父类）

​    │   

​    ├─entity         //实体相关

​    │   Administrator.java

​    │   Author.java

​    │   Book.java

​    │   Category.java

​    │   Customer.java

​    │   Order.java

​    │   OrderBook.java

​    │   PublishHouse.java

​    │   Sha256.java

​    │   Stash.java

​    │   User.java

​    │   

​    ├─servlet           //前端交互相关

​    │   AccountServlet.java

​    │   AddAdminServlet.java

​    │   AddBookServlet.java

​    │   AddOrderBookServlet.java

​    │   AdminsServlet.java

​    │   AuthorDetailServlet.java

​    │   BookDetailServlet.java

​    │   ChangeAccountInfoServlet.java

​    │   ChangeOrderBookServlet.java

​    │   CountServlet.java（二维统计与导出功能）

​    │   CurrentOrderServlet.java

​    │   CustomersServlet.java

​    │   DeleteCustomerServlet.java

​    │   DeleteSelfServlet.java

​    │   HistoryOrdersServlet.java

​    │   HomeServlet.java

​    │   LoginServlet.java

​    │   MoveCurrentOrderBookServlet.java

​    │   PayOrderServlet.java

​    │   PressDetailServlet.java

​    │   RegisterServlet.java

​    │   

​    └─util           //辅助类

​        dbConnectUtil.java