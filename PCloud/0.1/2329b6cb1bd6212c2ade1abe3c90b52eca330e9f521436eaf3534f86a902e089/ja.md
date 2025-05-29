```
file_pwrite(client::PCloudClient; kwargs...)
```

ファイルディスクリプタ `fd` に送信したデータをできるだけ書き込みます。データは、パラメータとして提供された `offset` で書き込まれます。

file*pwrite は O*APPEND フラグを無視します。ファイルのオフセットは変更されません。

データの送信方法については、こちらをご覧ください。

出典: https://docs.pcloud.com/methods/fileops/file_pwrite.html

# 引数

  * `fd::Int`: データが書き込まれるファイルディスクリプタ
  * `offset::Int`: データが書き込まれるバイト単位のオフセット

# 出力

書き込まれた `bytes`（バイト数）を返します。

# 出力例

```
{
    result: 0,
    bytes: 124
}
```
