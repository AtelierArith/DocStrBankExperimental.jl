```
deletefile(client::PCloudClient; kwargs...)
```

`fileid` または `path` で識別されるファイルを削除します。

ソース: https://docs.pcloud.com/methods/file/deletefile.html

# 引数

  * `fileid::Int`: 削除されたファイルのID
  * `path::String`: 削除されたファイルのパス

fileid または path を使用

# 出力

成功した場合、`isdeleted` が設定されたファイルの `metadata` を返します。

# 出力例

```
{
    "result": 0,
    "id": "139-0",
    "metadata": {
        "isfolder": false,
        "icon": "image",
        "size": 15604,
        "name": "Simple image.jpg",
        "category": 1,
        "contenttype": "image/jpeg",
        "parentfolderid": 0,
        "isdeleted": true,
        "hash": 6306013028049022731,
        "ismine": true,
        "isshared": false,
        "id": "f1736716",
        "height": 300,
        "width": 222,
        "modified": "Wed, 02 Oct 2013 16:00:40 +0000",
        "thumb": true,
        "created": "Wed, 02 Oct 2013 15:57:13 +0000",
        "fileid": 1736716
    }
}
```
