```
uploadlinkprogress(client::PCloudClient; kwargs...)
```

アップロードされたファイルの進行状況を監視します。

ソース: https://docs.pcloud.com/methods/upload_links/uploadlinkprogress.html

# 引数

  * `code::String`: アップロードリンクのコード
  * `progresshash::String`: uploadtolinkに渡される監視用のハッシュ

# 出力

`files`を除いたuploadprogressと同じデータを返します。
