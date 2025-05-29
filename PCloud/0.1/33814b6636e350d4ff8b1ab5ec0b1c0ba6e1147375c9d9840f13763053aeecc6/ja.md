```
file_write(client::PCloudClient; kwargs...)
```

ファイルディスクリプタ `fd` に送信したデータを現在のファイルオフセットに書き込み、オフセットを調整します。

データの送信方法については、こちらをご覧ください。

ソース: https://docs.pcloud.com/methods/fileops/file_write.html

# 引数

  * `fd::Int`: データが書き込まれるファイルディスクリプタ

# 出力

書き込まれた `bytes`（バイト数）を返します。

# 出力例

```
{
    result: 0,
    bytes: 124
}
```
