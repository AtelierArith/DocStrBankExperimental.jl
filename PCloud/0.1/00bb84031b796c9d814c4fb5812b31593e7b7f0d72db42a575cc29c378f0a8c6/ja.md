```
revertrevision(client::PCloudClient; kwargs...)
```

`fileid`/`path` と `revisionid` をパラメータとして受け取り、ファイルを指定されたリビジョンに戻します。

現在のファイルの内容は新しいリビジョンとして保存されます。

Source: https://docs.pcloud.com/methods/revisions/revertrevision.html

# 引数

  * `fileid::Int`: 戻されたファイルのID
  * `path::String`: 戻されたファイルのパス
  * `revisionid::Int`: ファイルが戻されるリビジョンのID

`fileid` または `path` を使用してください。

# 出力

成功した場合、新しいファイルのメタデータが返されます。
