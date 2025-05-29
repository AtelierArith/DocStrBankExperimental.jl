```
feedback(client::PCloudClient; kwargs...)
```

pCloudサポートにメッセージを送信します

ソース: https://docs.pcloud.com/methods/general/feedback.html

# 引数

  * `mail::String`: ユーザーのメールアドレス
  * `reason::String`: リクエストの件名
  * `message::String`: メッセージ自体

# オプション引数

  * `name::String`: ユーザーのフルネームを提供できます

# 出力例

```
{
    result: 0
}
```
