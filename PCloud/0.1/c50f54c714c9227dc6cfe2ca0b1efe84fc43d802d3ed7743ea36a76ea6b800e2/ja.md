```
trash_list(client::PCloudClient; kwargs...)
```

`Trash`内のフォルダの内容をリストします。

`Trash`のルートフォルダの`id`は`0`です。

フォルダの`metadata`を出力します。このメタデータには、フォルダの内容のメタデータの配列である`contents`フィールドがあります。

この関数からのメタデータには、ファイルまたはフォルダが`Trash`に移動される前に存在していたフォルダを示す追加のフィールド`origparentfolderid`があります。

したがって、`parentfolderid`フィールドは`Trash`内の位置を示しています。

現在のユーザーに属するファイルとフォルダのみがこのメソッドから出力されます。

`Trash`フォルダを再帰的にリストすることは高コストな操作ではありません。

このメソッドは`listfolder`に非常に似ています。

出典: https://docs.pcloud.com/methods/trash/trash_list.html

# オプション引数

  * `folderid::Int`: `Trash`フォルダのID。デフォルトは0 - `Trash`のルートです。
  * `nofiles::Int`: 設定されている場合、ファイルは`Trash`リストに含まれず、フォルダのみが含まれます。
  * `recursive::Int`: 設定されている場合、リストは再帰的になります - サブフォルダにはそのフォルダとファイルが含まれます。

# 出力

成功した場合、`Trash`からフォルダの`metadata`と`contents`を返します。

# 出力例

```
{
    result: 0,
    metadata: {
        thumb: false,
        path: "/",
        isfolder: true,
        isshared: false,
        ismine: true,
        modified: "Mon, 16 Sep 2013 12:10:32 +0000",
        created: "Mon, 16 Sep 2013 12:10:32 +0000",
        name: "/",
        folderid: 0,
        isdeleted: true,
        icon: "folder",
        id: "d0",
        contents: [
            {
                name: "Deleted folder",
                folderid: 236427,
                id: "d236427",
                origparentfolderid: 123,
                parentfolderid: 0,
                thumb: false,
                isfolder: true,
                isshared: false,
                ismine: true,
                modified: "Sat, 14 Dec 2013 13:37:33 +0000",
                created: "Tue, 03 Dec 2013 15:50:22 +0000",
                isdeleted: true,
                icon: "folder",
                contents: [ ]
            },
            {
                name: "Deleted file",
                id: "f76543",
                fileid: 76543,
                origparentfolderid: 6543,
                parentfolderid: 0,
                category: 3,
                icon: "audio",
                contenttype: "audio/x-mpegurl",
                hash: 17079372075467340000,
                size: 759,
                isfolder: false,
                thumb: false,
                isshared: false,
                modified: "Wed, 18 Sep 2013 10:18:46 +0000",
                created: "Wed, 18 Sep 2013 10:18:14 +0000",
                ismine: true,
                isdeleted: true
            }
        ]
    }
}
```
