```
createfolderifnotexists(client::PCloudClient; kwargs...)
```

フォルダーが存在しない場合はフォルダーを作成し、既存のフォルダーのメタデータを返します。

`path` 文字列パラメータ（推奨されていません）または int `folderid` と string `name` パラメータのいずれかを期待します。

ソース: https://docs.pcloud.com/methods/folder/createfolderifnotexists.html

# 引数

  * `path::String`: フォルダーへのパス（推奨されていません）
  * `folderid::Int`: フォルダーのID
  * `name::String`: フォルダーの名前

`path` または `folderid` + `name` を使用してください。

# 出力

成功した場合、`metadata` 構造体を返します。

# 出力例

```
{
    "result": 0,
    "created": true,
    "metadata": {
        "created": "Wed, 02 Oct 2013 13:11:53 +0000",
        "isfolder": true,
        "parentfolderid": 0,
        "icon": "folder",
        "id": "d230807",
        "path": "/new folder",
        "modified": "Wed, 02 Oct 2013 13:11:53 +0000",
        "thumb": false,
        "folderid": 230807,
        "isshared": false,
        "ismine": true,
        "name": "New folder"
    }
}
```
