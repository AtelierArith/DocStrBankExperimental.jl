```
collection_rename(client::PCloudClient; kwargs...)
```

現在のユーザーが所有する特定のコレクションの名前を変更します。

ソース: https://docs.pcloud.com/methods/collection/collection_rename.html

# 引数

  * `collectionid::Int`: コレクションのID。
  * `name::String`: コレクションの新しい名前。

# 出力

成功した場合、変更された `collection` を返します。

# 出力例

```
{
    "result": 0,
    "collection": [
        {
            "name": "my music",
            "id": 40,
            "ismine": true,
            "items": 8,
            "system": false,
            "type": "audio",
            "created": "Thu, 13 Feb 2014 12:34:22 +0000",
            "modified": "Mon, 17 Feb 2014 11:25:55 +0000",
            "contents": [ ]
        }
    ]
}
```
