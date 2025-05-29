```
copytolink(client::PCloudClient; kwargs...)
```

現在のユーザーのファイルシステムからアップロードリンクにファイルをコピーします。

ソース: https://docs.pcloud.com/methods/upload_links/copytolink.html

# 引数

  * `code::String`: アップロードリンクのコード
  * `fileid::Int`: コピーされたファイルのID
  * `path::String`: コピーされたファイルのパス

「fileid」または「path」を使用してください。

# オプション引数

toname "string" コピーされたファイルを保存するための名前。提供されていない場合は、ファイルの名前が使用されます。
