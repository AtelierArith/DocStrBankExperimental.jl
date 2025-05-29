```
collection_list(client::PCloudClient; kwargs...)
```

現在のユーザーが所有するコレクションのリストを取得します。

オプションとして、コレクション内のアイテムを返すことができ、コレクションをタイプでフィルタリングすることもできます。

現在のユーザーのシステムコレクションは、このメソッドの最初の呼び出し時に生成されます。

このメソッドは、呼び出し時に見つからなかったアイテムをコレクションから削除します。理由としては、ファイルがゴミ箱に移動された、または現在は共有されていない共有フォルダーにあったなどがあります。

出典: https://docs.pcloud.com/methods/collection/collection_list.html

# オプション引数

  * `type::Int`: コレクションのタイプをフィルタリングします。1はプレイリスト用です。
  * `showfiles::Int`: 設定されている場合、コレクションの内容はコレクション内のファイルのメタデータで満たされます。
  * `pagesize::Int`: 設定されていて、showfilesが設定されている場合、内容内のアイテムはこの数に制限されます。

# 出力

成功した場合、`collections`とオプションでコレクション内の最初のアイテムのメタデータが`contents`フィールドに返されます。

# 出力例

```
{
    "result": 0,
    "collections": [
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
        } ,
        { 
            "name": "Most Listened",
            "id": 38,
            "ismine": true,
            "items": 0,
            "system": true,
            "type": "audio",
            "created": "Wed, 12 Feb 2014 11:51:00 +0000",
            "modified": "Wed, 12 Feb 2014 11:51:00 +0000",
            "contents": [ ]
        } ,

        ...

    ]
}
```
