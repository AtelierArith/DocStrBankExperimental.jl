```
collection_details(client::PCloudClient; kwargs...)
```

指定されたコレクションとその中のアイテムの詳細を取得します。

オプションで、コレクション内の結果に対してページングを使用することができます。

このメソッドは、呼び出し時に見つからなかったすべてのアイテムをコレクションから削除します。理由としては、ファイルがゴミ箱に移動された、または現在は共有されていない共有フォルダにあったなどがあります。そのため、ページングが使用される場合、ページにはページサイズよりも少ない結果が含まれる可能性があり、さらに利用可能なページが存在することがあります。

ソース: https://docs.pcloud.com/methods/collection/collection_details.html

# 引数

  * `collectionid::Int`: コレクションのID。

# オプションの引数

  * `page::Int`: 結果が表示されるページの番号。
  * `pagesize::Int`: ページのサイズ。

デフォルトのページは0で、すべてのアイテムが含まれます。

# 出力

成功した場合、`collection`と`contents`フィールド内のアイテムの`metadata`を返します。

# 出力例

```
{
    "result": 0,
    "collection": {
        "id": 40,
        "type": "audio",
        "system": false,
        "ismine": true,
        "items": 11,
        "created": "Thu, 13 Feb 2014 12:34:22 +0000",
        "modified": "Tue, 18 Feb 2014 11:16:24 +0000",
        "name": "my music",
        "contents": [
            {
                "id": "f599457",
                "fileid": 599457,
                "name": "Demo Audio 2.mp3",
                "parentfolderid": 21383,

                "position": 1,
                "added": "Mon, 17 Feb 2014 15:53:48 +0000",

                "isshared": false,
                "category": 3,
                "ismine": true,
                "icon": "audio",
                "created": "Mon, 16 Sep 2013 12:10:32 +0000",
                "hash": 1682158607045670700,
                "isfolder": false,
                "contenttype": "audio/mpeg",
                "modified": "Mon, 16 Sep 2013 12:10:32 +0000",
                "size": 142376,
                "thumb": false
            },

            ...

        ]
    }
}
```
