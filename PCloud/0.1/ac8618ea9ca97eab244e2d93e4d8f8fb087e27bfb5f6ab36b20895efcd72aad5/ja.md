```
changeshare(client::PCloudClient; kwargs...)
```

共有の権限を変更します。

権限はsharefolderと同じです。

共有/フォルダの所有者のみがこのメソッドを使用できます。

つまり、*アウトゴーイング* 共有のみに許可されています。

出典: https://docs.pcloud.com/methods/sharing/changeshare.html

# 引数

  * `shareid::Int`: listsharesによって返される共有リクエストのID
  * `permissions::String`: 新しい権限

# 出力例

```
{
    "result": 0
}
```
