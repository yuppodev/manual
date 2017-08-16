# 轮播视频流接入

### HLS动态URL

为了防止爬虫恶意盗流，m3u8网址都是计算出来的，有效期时间最长30分钟

示例

> http://video.iqucang.com/channel/1502883021/2WILiOybJSr3k-ltk_knHw/abcdefghijklmnopqrstuvwxyz123456/hdphd.m3u8

如果已经失效，会提示410

### 计算方式
```
expires
    过期时间戳，Unix时间戳，单位秒，有效范围为当前时间到未来30分钟，建议取未来15-20分钟，客户端时间错乱会造成无法播放
deviceid
    设备ID或者用户ID，要求使用md5值，32位，系统内要求唯一，流服务器会限制单设备频繁请求
stream
    指定的流标识编号，每个媒体渠道的视频流标识别可能不通，请联系商务人员获取
password
    加密密码，由服务器分发，不定期更新。请联系商务人员获取
md5
    为expires＋device_id＋stream＋password组成的源串，进行md5加密后，对数据进行base64编码并过滤获得。加密及校验工具请联系商务人员获取
```

最后组合成一个URL

http://video.iqucang.com/channel/**expires**/**md5**/**deviceid**/**stream**.m3u8




