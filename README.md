# 小小影视

> 代码已同时兼容 Surge & QuanX, 使用同一份签到脚本即可

> 目前分开两个版本，一个是完整版8任何同时执行，但是可能会存在偶尔到点抽风不执行（签到，广告，分享，评论，10次观影，5次收藏，30分钟连续观影，每日22点开宝箱）

## 配置 (QuanX)
```properties
[MITM]

小小影视版的域名太多了，自行抓包看域名添加吧。

[rewrite_local]

# 189及以前版本
^https:\/\/.*\..*\.com\/ucp\/index url script-response-body xxys.cookie.js
# 190及以后版本
^https:\/\/.*\..*\.com\/ucp\/index url script-request-header xxys.cookie.js

[task_local]

## 完整版执行请严格按下面格式

*/10 0-30 9,22 * * * xxysrw.js

## 多任务版本不限时间格式(9点执行6任务，22点执行开箱)

0 9,22 * * * xxys_6rw.js

## 连续观影30分钟的任务，分钟时间必须0-30分钟

*/10 0-30 9 * * * xxys_play.js
```
## 说明

1. 登陆小小影视APP，点击“我的”，自动获取到cookie，就可以注释获取cookie脚本了


## 常见问题

1. 无法写入 Cookie

   - 请查看配置的mitm是否正确，可以抓包看域名。

2. 写入 Cookie 成功, 但签到不成功

   - 看看是否因为task的任务执行时间错了。

3. 为什么有时成功有时失败

   - 很正常，网络问题，因为执行的时候网络卡一下，跳过了配对时间执行不会生效，尤其是完整版。



