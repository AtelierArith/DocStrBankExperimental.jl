```
pcloud_stat(client::PCloudClient; kwargs...)
```

`stat` APIメソッドは、`fileid`または`path`で指し示されるファイルに関する情報を返します。`fileid`を使用することを推奨します。

ソース: https://docs.pcloud.com/methods/file/stat.html

# 引数

  * `path::String`: ファイルへのパス（推奨されません）
  * `fileid::Int`: ファイルのID

# 出力

メタデータを返します。

# 出力例

```
{
    "result": 0,
    "metadata": {
      "ismine": true,
      "id": "f1729212",
      "created": "Wed, 02 Oct 2013 14:29:11 +0000",
      "modified": "Wed, 02 Oct 2013 14:29:11 +0000",
      "hash": 10681749967730527559,
      "isshared": false,
      "isfolder": false,
      "category": 1,
      "parentfolderid": 0,
      "icon": "image",
      "fileid": 1729212,
      "height": 600,
      "width": 900,
      "path": "/Simple image.jpg",
      "name": "Simple image.jpg",
      "contenttype": "image/jpeg",
      "size": 73269,
      "thumb": true
    }
}

```
