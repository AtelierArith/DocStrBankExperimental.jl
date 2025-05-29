```
changeuploadlink(client::PCloudClient; kwargs...)
```

`uploadlinkid`で識別されるアップロードリンクを変更します。

変更可能なオプションには以下が含まれます：

有効期限

アップロードリンクのスペース

アップロードリンクのファイル

Source: https://docs.pcloud.com/methods/upload_links/changeuploadlink.html

# 引数

  * `uploadlinkid::Int`: アップロードリンクのID

# オプション引数

  * `expire::datetime`: リンクの有効期限を設定
  * `deleteexpire::Int`: 設定されている場合、リンクの有効期限が削除されます
  * `maxspace::Int`: リンクの最大利用可能スペース（バイト単位）を変更
  * `maxfiles::Int`: リンクの最大利用可能ファイル数を変更

`maxspace`または`maxfiles`を`0`に設定すると、指定された制限が削除されます。
