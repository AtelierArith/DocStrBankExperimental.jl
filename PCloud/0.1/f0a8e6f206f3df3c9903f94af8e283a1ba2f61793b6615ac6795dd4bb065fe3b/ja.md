```
trash_restorepath(client::PCloudClient; kwargs...)
```

`Trash`から復元したいファイルまたはフォルダの復元先を計算します。

このメソッドは、`ismine`が`true`であるような宛先フォルダを選択することが保証されています。

親フォルダも削除されている場合、このメソッドはフォルダの親に移動することでパスを計算します。これにより、ファイルまたはフォルダはファイルシステムのルートに復元されることになります。

また、名前の衝突がある場合は、同じ名前のファイルが`k-1`個ある場合に`Name (k)`という新しい名前が生成されます。

出典: https://docs.pcloud.com/methods/trash/trash_restorepath.html

# 引数

  * `fileid::Int`: 復元されるファイルのファイルID
  * `folderid::Int`: 復元されるフォルダのフォルダID

`fileid`または`folderid`を使用してください。

# 出力

成功した場合、次の`metadatas`が返されます。

  * `metadata`: ファイルまたはフォルダが復元後にどのように見えるかに関する情報
  * `destination`: 復元されたフォルダの計算された宛先に関する情報

# 出力例

```
{
    result: 0,
    metadata: {
        name: "削除されたフォルダ",
        id: "d56986",
        folderid: 56986,
        parentfolderid: 56980,
        isdeleted: true,
        ismine: true,
        icon: "folder",
        created: "Mon, 03 Feb 2014 15:02:56 +0000",
        modified: "Mon, 03 Feb 2014 15:03:13 +0000",
        isfolder: true,
        thumb: false,
        isshared: true
    },
    destination: {
        name: "宛先フォルダ",
        id: "d56980",
        folderid: 56980,
        parentfolderid: 0,
        ismine: true,
        icon: "folder",
        created: "Fri, 31 Jan 2014 12:57:56 +0000",
        modified: "Mon, 03 Feb 2014 15:04:32 +0000",
        isfolder: true,
        thumb: false,
        isshared: true
    }
}
```
