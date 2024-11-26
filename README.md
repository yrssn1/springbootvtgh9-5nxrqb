# springboot005学生心理咨询评估系统

## 简介

本代码仅供学习参考使用

加QQ(**3055269939**)免费获取项目和论文

## 主要内容

### ***\*数据库\*******\*表\*******\*结构设计\****

本次程序开发选用的数据库管理工具是MySQL数据管理工具，使用它存放数据也需要创建程序对应的数据库文件，并命名刚创建的数据库文件，有了数据库也需要创建各种数据表来充实数据库，在数据表的创建中，不仅需要对数据表命名，也需要对数据表的字段进行设计，包括每个数据表里面需要设置的字段名称，字段对应的数据类型信息，字段的主键设置这个也是不可缺少的，因为每个数据表里面的主键就是标记着这个数据表跟其他数据表相区分的唯一标志。就相当于生活中的每个人都有姓名，但是上网搜索自己的名字，会发现全国上下有很多人的名字跟自己的名字一模一样，包括姓氏以及名字，区分每个人的唯一信息就是每个人的身份证号信息，主键在数据表里面也是起着这样的重要作用。下面就介绍本次开发的程序学生心理咨询评估系统的数据表结构信息。

表4.1 试卷表

| 字段      | 类型         | 空   | 默认              | 注释           |
| --------- | ------------ | ---- | ----------------- | -------------- |
| id (主键) | bigint(20)   | 否   |                   | 主键           |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间       |
| name      | varchar(200) | 否   |                   | 试卷名称       |
| time      | int(11)      | 否   |                   | 考试时长(分钟) |
| status    | int(11)      | 否   | 0                 | 试卷状态       |

表4.2 试题表

| 字段         | 类型         | 空   | 默认              | 注释                                                         |
| ------------ | ------------ | ---- | ----------------- | ------------------------------------------------------------ |
| id (主键)    | bigint(20)   | 否   |                   | 主键                                                         |
| addtime      | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间                                                     |
| paperid      | bigint(20)   | 否   |                   | 所属试卷id（外键）                                           |
| papername    | varchar(200) | 否   |                   | 试卷名称                                                     |
| questionname | varchar(200) | 否   |                   | 试题名称                                                     |
| options      | longtext     | 是   | NULL              | 选项，json字符串                                             |
| score        | bigint(20)   | 是   | 0                 | 分值                                                         |
| answer       | varchar(200) | 是   | NULL              | 正确答案                                                     |
| analysis     | longtext     | 是   | NULL              | 答案解析                                                     |
| type         | bigint(20)   | 是   | 0                 | 试题类型，0：单选题 1：多选题 2：判断题 3：填空题（暂不考虑多项填空） |
| sequence     | bigint(20)   | 是   | 100               | 试题排序，值越大排越前面                                     |

表4.3 考试记录表

| 字段         | 类型         | 空   | 默认              | 注释             |
| ------------ | ------------ | ---- | ----------------- | ---------------- |
| id (主键)    | bigint(20)   | 否   |                   | 主键             |
| addtime      | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间         |
| userid       | bigint(20)   | 否   |                   | 用户id           |
| username     | varchar(200) | 是   | NULL              | 用户名           |
| paperid      | bigint(20)   | 否   |                   | 试卷id（外键）   |
| papername    | varchar(200) | 否   |                   | 试卷名称         |
| questionid   | bigint(20)   | 否   |                   | 试题id（外键）   |
| questionname | varchar(200) | 否   |                   | 试题名称         |
| options      | longtext     | 是   | NULL              | 选项，json字符串 |
| score        | bigint(20)   | 是   | 0                 | 分值             |
| answer       | varchar(200) | 是   | NULL              | 正确答案         |
| analysis     | longtext     | 是   | NULL              | 答案解析         |
| myscore      | bigint(20)   | 否   | 0                 | 试题得分         |
| myanswer     | varchar(200) | 是   | NULL              | 考生答案         |

表4.4 管理员表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| username  | varchar(100) | 否   |                   | 用户名   |
| password  | varchar(100) | 否   |                   | 密码     |
| role      | varchar(100) | 是   | 管理员            | 角色     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 新增时间 |

表4.5 用户

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| zhanghao  | varchar(200) | 否   |                   | 账号     |
| mima      | varchar(200) | 否   |                   | 密码     |
| xingming  | varchar(200) | 是   | NULL              | 姓名     |
| xingbie   | varchar(200) | 是   | NULL              | 性别     |
| shouji    | varchar(200) | 是   | NULL              | 手机     |
| youxiang  | varchar(200) | 是   | NULL              | 邮箱     |
| zhaopian  | varchar(200) | 是   | NULL              | 照片     |
| beizhu    | longtext     | 是   | NULL              | 备注     |