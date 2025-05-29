```
collection_create(client::PCloudClient; kwargs...)
```

現在のユーザーのために新しいコレクションを作成します。

オプションとして、コレクションを埋めるためのファイルを指定することができます。

ソース: https://docs.pcloud.com/methods/collection/collection_create.html

# 引数

  * `name::Int`: 新しいコレクションの名前。

# オプション引数

  * `type::Int`: コレクションのタイプ。
  * `fileids::String`: コレクションを埋めるためのファイルのカンマ区切りリスト。

デフォルトのタイプは1 - プレイリストです。

# 出力

成功した場合、新しい `collection` と、フィールド `contents` に与えられたアイテムの `metadata` を返します。

また、コレクションを埋めるためのファイルがあった場合、フィールド `linkresult` が追加されます。その構造については `collection_linkfiles` を参照してください。リンクが成功しなかった場合、このフィールドは `false` になります。

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
