# 今日头条接口

#### 接口说明
* 账号注册请联系qq:1628121385，添加好友时请注明:wxapi
* url请求需带上参数key，每个用户有唯一的key。
* 所有接口均返回json格式，其中参数ok[true|false]表示是否请求成功.
* retCode为返回码，详情参考[返回码说明](https://github.com/iwoods100/wxapi-doc/blob/master/retcode.md)
* 当返回ok=false时，可以参考返回的error字段（如果存在的话）
* 一般来说，接口只要返回cost=true，就表示请求有效，会进行收费，此时请不要再重试了，这种情况一般是请求资源已经失效。

#### web版接口合集

```
http://whosecard.com:8081/api/toutiao/web?key=***&api=***&其它参数=***

本接口根据不同的api参数，调用不同的数据接口，统一返回格式如下：
{
  "ok": true,
  "result": {
    ... # 返回值与官方接口一样，字段比较多，按字面意思理解即可
  }
}

以下是各数据接口定义：

用户基础信息：
api=user_info
user_id=用户id，如 3253636303

自媒体热文列表：
api=media_hot
media_hot=自媒体id，如 3253671606

单个文章/视频信息：
api=item_info
item_id=文章/视频id，如 6680829865307931139

单个文章/视频评论：
api=item_comment
item_id=文章/视频id，如 6680829865307931139
offset：默认为0，每次返回10条，以此加10
注意：本web接口最多返回前20条评论信息

关键字搜索：
api=search
keyword=关键字，如 vlog
offset：翻页，取上一页请求的offset返回值作为下一页offset参数
search_type：搜索类型（1是综合，2是视频，4是用户，默认为1）
```
