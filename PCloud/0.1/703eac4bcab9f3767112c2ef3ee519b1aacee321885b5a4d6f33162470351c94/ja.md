```
trash_restore(client::PCloudClient; kwargs...)
```

`Trash` からファイルやフォルダをファイルシステムに復元します。

データが復元される先は、trash_restorepath を介して自動的に計算されるか、ユーザーによって指定されることがあります（`restoreto` パラメータを使用）。

`folderid='0'` の場合、`Trash` 内のすべてのデータができるだけ元の位置に復元されます。`restoreto` が設定されている場合、`Trash` 内のすべてのデータはこのフォルダに配置されます。

宛先が共有フォルダの場合、そのフォルダが共有されているユーザーは、そのフォルダに対して CREATE アクセスが必要です。

現在のユーザーが使用しているスペース + 復元されたファイルのサイズがユーザーのクォータを超える場合、このメソッドは、クォータを超える最初のファイルが復元されるまで復元を行います。その後、エラーが発生します。

出典: https://docs.pcloud.com/methods/trash/trash_restore.html

# 引数

  * `fileid::Int`: 復元されたファイルのファイル ID
  * `folderid::Int`: 復元されたフォルダのフォルダ ID

`fileid` または `folderid` を使用

# オプション引数

  * `restoreto::Int`: 指定された場合、このフォルダが復元されたデータの宛先として選択されます。
  * `metadata::Int`: 設定されていてフォルダを復元する場合、復元されたフォルダ内のファイルやフォルダに関する情報で内容が埋められたフォルダのメタデータが生成されます。

# 出力

成功した場合、復元されたファイルまたはフォルダの `metadata` を返します。

`Trash` のルートが復元され、`restoreto` が指定されている場合、`restoreto` フォルダのメタデータが表示されます。

`restoreto` が指定されていない場合、結果は復元されたファイル/フォルダの `metadatas` のリスト `restored` です。

# 出力例

```
{
    result: 0,
    metadata: {
        name: "削除されたフォルダ",
        folderid: 236427,
        id: "d236427",
        parentfolderid: 0,
        thumb: false,
        isfolder: true,
        isshared: false,
        ismine: true,
        modified: "Sat, 16 Dec 2013 16:20:00 +0000",
        created: "Tue, 03 Dec 2013 15:50:22 +0000",
        isdeleted: false,
        icon: "folder",
        contents: [
        ]
    }
}
```
