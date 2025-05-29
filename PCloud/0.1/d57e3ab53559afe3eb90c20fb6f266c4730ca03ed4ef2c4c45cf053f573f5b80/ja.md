```
uploadprogress(client::PCloudClient; kwargs...)
```

ファイルのアップロード進行状況を取得します。

現在アップロード中の同じAPIサーバーに送信する必要があります。パラメータ文字列 `progresshash` は必ず渡す必要があり、現在進行中のアップロードリクエストで渡されたのと同じ値を含む必要があります。

出典: https://docs.pcloud.com/methods/file/uploadprogress.html

# 引数

  * `progresshash::String`: アップロードを定義するハッシュ、uploadfileに送信されたものと同じ

# 出力

成功した場合、次のフィールドが返されます:

  * `total`: 転送される合計バイト数（アップロードリクエストのContent-Length）
  * `uploaded`: これまでにアップロードされたバイト数
  * `currentfile`: 現在アップロード中のファイルのファイル名
  * `files`: すでにアップロードされたファイルのメタデータ（現在のファイルを除く）
  * `finished`: アップロードが完了したかどうかを示します

完了したアップロードの場合、`currentfile` と `currentfileuploaded` は存在しません。

`total` と `uploaded` にはプロトコルのオーバーヘッドとメタデータが含まれており、`currentfileuploaded` には含まれません。

# 出力例

```
{
    "currentfile": "Simple file",
    "currentfileuploaded": 4199743,
    "result": 0,
    "total": 7768889,
    "filenumber": 1,
    "uploaded": 4199936,
    "finished": false,
    "files": [ ]
}
```
