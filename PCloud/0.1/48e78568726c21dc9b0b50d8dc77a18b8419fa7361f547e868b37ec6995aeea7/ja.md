```
collection_unlinkfiles(client::PCloudClient; kwargs...)
```

現在のコレクションからファイルを削除します。

コレクションからファイルを削除する方法は3つあります：

すべてのアイテムをコレクションから削除するファイルIDをコレクションから削除する指定された位置にあるアイテムを削除する優先されるのは、位置、次にすべて、最後にファイルIDです。

出典: https://docs.pcloud.com/methods/collection/collection_unlinkfiles.html

# 引数

  * `collectionid::Int`: コレクションのID。

# オプション引数

  * `all::Int`: 設定されている場合、コレクションからすべてのファイルがリンク解除されます
  * `positions::String`: リンク解除される位置のカンマ区切りリスト
  * `fileids::String`: リンク解除されるファイルIDのカンマ区切りリスト

*注:* このパラメータのいずれかを使用してください。

# 出力

成功した場合、修正された `collection` を返します。

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
            "modified": "Mon, 18 Feb 2014 14:25:55 +0000",
            "contents": [ ]
        }
    ]
}
```
