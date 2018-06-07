## 灵悉 API

### 1. 概述
灵悉API采用POST请求，参数以from表单提交，不排除后续采用Json格式可以能
接口基础地址，以本地测试版为例：`http://localhost/lingxi-dev/`

### 2. 接口
#### 2.1 基础参数说明
##### 2.1.1 公共返回参数
| 参数名 | 类型   | 必填规则 | 说明     |
| ------ | ------ | -------- | -------- |
| code   | String | 必填     | 错误码   |
| msg    | Sgring | 必填     | 错误信息 |
| data   | Object | 非必填   | 返回数据 |
##### 2.1.2 公共分页参数
| 参数名   | 类型 | 必填规则 | 说明     |
| -------- | ---- | -------- | -------- |
| pageNum  | innt | 必填     | 当前页   |
| pageSize | int  | 必填     | 每页数量 |
| total    | int  | 必填     | 总条数   |
| size     | int  | 必填     | 当前页数 |
| list     | T[]  | 必填     | 结果集   |
##### 2.1.3 公共返回码信息
| 返回码 | 返回信息           | 备注         |
| ------ | ------------------ | ------------ |
| 00000  | 操作成功           | 成功         |
| 00001  | 操作失败           | 失败         |
| 00002  | 服务器内部错误     | 返回错误堆栈 |
| 00100  | 参数为空           | 需要参数时   |
| 00101  | id为空             | 查询对象时   |
| 00102  | id对应的对象不存在 | 查询对象时   |
| 00103  | 分页参数为空       | 用于分页查询 |

#### 2.2 用户相关
##### 2.2.1 注册
Url： `user/register`
请求参数
| 参数名   | 类型   | 必填规则 | 说明   |
| -------- | ------ | -------- | ------ |
| username | String | 必填     | 用户名 |
| phone    | String | 必填     | 手机号 |
| password | String | 必填     | 密码   |
返回参数
```
{
    "code": "00000",
    "msg": "操作成功",
    "data": {
        "id": "bef95afda1***",
        "uid": 10080,
        "username": "xyz",
        "phone": "11111111111",
        "sex": -1,
        "qq": "",
        "avatar": "user/image/a+=.jpg",
        "signature": "",
        "imToken": "WFYjwQPA3pY3deyv2****",
        "loginTime": "2018-05-30 21:57:56",
        "createTime": "2015-11-23 15:33:55",
        "updateTime": "2018-06-04 00:35:05"
    }
}
```
错误码
| 错误码 | 错误信息     | 备注 |
| ------ | ------------ | ---- |
| 00105  | 手机号已注册 |      |
| 00106  | 用户名已存在 |      |
