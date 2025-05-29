```
deletefolder(client::PCloudClient; kwargs...)
```

フォルダを削除します

`path` 文字列パラメータ（推奨されていません）または int `folderid` パラメータのいずれかを期待します。

*注:* `deletefolder` を呼び出す前に、フォルダは空でなければなりません。

ソース: https://docs.pcloud.com/methods/folder/deletefolder.html

# 引数

  * `path::String`: フォルダへのパス（推奨されていません）
  * `folderid::Int`: フォルダのID

# 出力

成功した場合、削除されたフォルダの `metadata` 構造体を返します。

# 出力例

```
{
    "result": 0,
    "id": "111-0",
    "metadata": {
        "icon": "folder",
        "parentfolderid": 0,
        "isfolder": true,
        "isdeleted": true,
        "created": "Wed, 02 Oct 2013 13:11:53 +0000",
        "modified": "Wed, 02 Oct 2013 13:31:49 +0000",
        "isshared": false,
        "name": "Simple Folder",
        "id": "d230807",
        "folderid": 230807,
        "ismine": true,
        "thumb": false
    }
}
```
