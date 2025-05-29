```
listfolder(client::PCloudClient; kwargs...)
```

フォルダのデータを受け取ります。

folderid または path パラメータを期待し、フォルダの `metadata` を返します。メタデータにはフォルダの内容のメタデータの配列である `contents` フィールドがあります。

ルートフォルダを再帰的にリストすることは高コストな操作ではありません。

出典: https://docs.pcloud.com/methods/folder/listfolder.html

# 引数

  * `path::String`: フォルダへのパス（推奨されません）
  * `folderid::Int`: フォルダのID

`path` または `folderid` を使用してください。

# オプション引数

  * `recursive::Int`: 設定されている場合、完全なディレクトリツリーが返され、すべてのディレクトリに内容フィールドが含まれます。
  * `showdeleted::Int`: 設定されている場合、削除されたファイルやフォルダで復元可能なものが表示されます。
  * `nofiles::Int`: 設定されている場合、フォルダの（サブ）構造のみが返されます。
  * `noshares::Int`: 設定されている場合、ユーザー自身のフォルダとファイルのみが表示されます。

# 出力

フォルダの `metadata` を返します。メタデータにはフォルダの内容のメタデータの配列である `contents` フィールドがあります。

# 出力例

```
{
    result: 0,
    metadata: {
        icon: "folder",
        id: "d0",
        modified: "Thu, 19 Sep 2013 07:31:46 +0000",
        path: "/",
        thumb: false,
        created: "Thu, 19 Sep 2013 07:31:46 +0000",
        folderid: 0,
        isshared: false,
        isfolder: true,
        ismine: true,
        name: "/",
        contents: [
            {
                parentfolderid: 0,
                id: "d230807",
                modified: "Wed, 02 Oct 2013 13:23:35 +0000",
                path: "/Simple Folder",
                thumb: false,
                created: "Wed, 02 Oct 2013 13:11:53 +0000",
                folderid: 230807,
                ismine: true,
                isshared: false,
                isfolder: true,
                name: "Simple Folder",
                icon: "folder"
            }, {
                icon: "audio",
                contenttype: "audio/mpeg",
                parentfolderid: 0,
                modified: "Wed, 02 Oct 2013 13:23:19 +0000",
                path: "/Simple Audio.mp3",
                hash: 5380817599554757000,
                thumb: false,
                created: "Wed, 02 Oct 2013 13:23:19 +0000",
                id: "f1723778",
                ismine: true,
                category: 3,
                fileid: 1723778,
                isshared: false,
                isfolder: false,
                name: "Simple Audio.mp3",
                size: 11252576
            }]
    }
}
```
