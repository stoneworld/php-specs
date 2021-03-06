# [`<h1>` 项目名称] API 接口文档[模板]

## 1. 项目简介

[ 简要说明项目的来龙去脉，并对接口文档适用对象作简要说明。]

| 项目     | 内容           |
|----------|----------------|
| 系统名称 | [project name] |
| 负 责 人 | [PM name]      |
| 提交日期 | [2016-04-01]   |

## 2. 开发人员列表

开发人员列表

| 姓名   | 职位       | Git user.name | Git user.email         |
|--------|------------|---------------|------------------------|
| 胡志飞 | 开发工程师 | WisdomFusion  | WisdomFusion#gmail.com |
| ...    |            |               |                        |

## 3. CHANGELOG

| 版本号 | 修改内容简介 |   修改日期 | 修改人       |
|--------|--------------|------------|--------------|
|    1.0 | 说明         | 2016-04-01 | WisdomFusion |
|    ... |              |            |              |

## 4. 名词解释

无

## 5. 通信约定

无

## 6. 错误码定义

每个响应的返回数据中，成功则先添加一个 `success:true` 的字段，错误即返回错误码，错误码定义：

| error_code | error_msg                       | 描述                     |
|------------|---------------------------------|--------------------------|
|          1 | Unknown error                   | 未知错误                 |
|          2 | Service temporarily unavailable | 服务暂时不可用           |
|          3 | Unsupported API method          | API 接口不被支持         |
|          4 | API request limit reached       | 请求数达到上限           |
|          5 | Unauthorized client IP address  | API 调用端的 IP 未被授权 |
|        100 | Invalid parameter               | 参数无效或数数数量不符   |
|        101 | Invalid API key                 | API key 无效             |
|        ... |                                 |                          |

## 7. 接口说明

### `<h3>` 获取用户信息

* **功能：**获取用户信息

* **请求方法：**GET

* **请求URL：**/api/user

* **请求参数：**

  | 参数名 | 必选 | 类型   | 描述                        |
  |--------|------|--------|-----------------------------|
  | userid | Y    | int    | 用户 ID，不可为空           |
  | format | Y    | string | 返回数据的格式，json 或 xml |

* **响应参数：**

  返回数据 user
  
  | 字段名       | 描述         |
  |--------------|--------------|
  | accout       | 用户账户     |
  | version      | 版本信息     |
  | expired_time | 到期时间     |
  | space        | 用户空间信息 |
  | traffic      | 用户流量信息 |
  
  space 包含字段列表：
  
  | 字段名 | 描述                     |
  |--------|--------------------------|
  | total  | 用户空间总量，单位 G     |
  | remain | 用户空间剩余量，单位 G   |
  | used   | 用户空间使用总量，单位 G |
  
  traffic 包含字段列表：
  
  | 字段名 | 描述                     |
  |--------|--------------------------|
  | total  | 用户空间总量，单位 G     |
  | remain | 用户空间剩余量，单位 G   |
  | used   | 用户空间使用总量，单位 G |
  
* **错误码：**

  当前接口错误码列表，上文“错误码定义”一节已定义通用错误码列表。如果没有的话，省略此项。

* **示例：**

  XML 格式的响应信息如下：
  
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <success>true</success>
  <user>
    <account>test@test.com</account>
    <version><![CDATA[用户版]]></version>
    <expired>2011-06-06</expired>
    <space>
      <total>2</total>
      <remain>1.9</remain>
      <used>0.1</used>
    </space>
    <traffic>
      <total>5</total>
      <remain>4.8</remain>
      <used>0.2</used>
    </traffic>
  </user>
  ```
  JSON 格式的响应信息如下：
  
  ```json
  {
    "success":true,
    "user":{
      "account":"test@test.com",
      "version":"试用版",
      "expired":"2011-06-06",
      "space":{
        "total":2,
        "remain":1.9,
        "used":0.1
      },
      "traffic":{
        "total":5,
        "remain":4.8,
        "used":0.2
      }
    }
  }
  ```
