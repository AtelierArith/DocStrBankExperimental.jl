```
collection_linkfiles(client::PCloudClient; kwargs...)
```

コレクションにファイルを追加します。

ファイルはコレクションの最後に追加されます。別の位置にファイルを挿入したい場合は、このメソッドを介してリンクし、その後 `collection_move` を使用してください。

このメソッドは、fileids フィールドに指定された相対的な順序を保持します。

コレクション内で重複は許可されていません。

出典: https://docs.pcloud.com/methods/collection/collection_linkfiles.html

# 引数

  * `collectionid::Int`: コレクションの ID。
  * `fileids::String`: 追加するファイルの ID のカンマ区切りリスト。

# オプション引数

  * `noitems::Int`: 設定されている場合、linkresult は空になります。

# 出力

成功した場合、更新された `collection` を返します。

`linkresult` には、すべてのアイテムの結果が含まれます。`noitems` が設定されている場合は除きます。フォーマットは次のとおりです。

  * `result::Int`: 操作のコード。0 は成功を意味し、それ以外はファイルをリンクできなかったことを示します。
  * `fileid::Int`: リンクされたファイルの ID
  * `message::String`: エラーが発生した場合、これはエラーメッセージです。成功した場合は設定されません。
  * `metadata::metadata`: リンクが成功した場合のリンクされたファイルのメタデータ。追加されるフィールドは次のとおりです: position - アイテムがコレクションに追加される位置 added - アイテムがコレクションにリンクされた日時

# 出力例

```
{
    "result": 0,
    "linkresult": [
    {
        "fileid": "599457",
        "result": 0,
        "metadata": {
            "id": "f599457",
            "fileid": 599457,
            "contenttype": "audio/mpeg",

            "position": 9,
            "added": "Tue, 18 Feb 2014 11:16:24 +0000",

            "created": "Mon, 16 Sep 2013 12:10:32 +0000",
            "modified": "Mon, 16 Sep 2013 12:10:32 +0000",
            "hash": 1682158607045670700,
            "icon": "audio",
            "parentfolderid": 21383,
            "ismine": true,
            "isshared": false,
            "isfolder": false,
            "name": "Demo Audio 2.mp3",
            "category": 3,
            "thumb": false,
            "size": 1442376
        }
    },
    {
        "fileid": "123",
        "result": 2009,
        "message": "File not found."
    },

    ...

    ],
    "collection": {
        "id": 40,
        "name": "my music",
        "type": "audio",
        "ismine": true,
        "system": false,
        "items": 11,
        "created": "Thu, 13 Feb 2014 12:34:22 +0000",
        "modified": "Tue, 18 Feb 2014 11:16:24 +0000",
        "contents": []
    }
}
```
