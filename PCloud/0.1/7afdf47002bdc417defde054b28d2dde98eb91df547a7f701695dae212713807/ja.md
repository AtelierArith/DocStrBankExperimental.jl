```
deletefolderrecursive(client::PCloudClient; kwargs...)
```

フォルダを削除します

`path` 文字列パラメータ（推奨されていません）または int `folderid` パラメータのいずれかを期待します。

*注意:* この関数はファイル、ディレクトリを削除し、共有を解除します。極めて注意して使用してください。

ソース: https://docs.pcloud.com/methods/folder/deletefolderrecursive.html

# 引数

  * `path::String`: フォルダへのパス（推奨されていません）
  * `folderid::Int`: フォルダのID

# 出力

成功した場合、int `deletedfiles` - 削除されたファイルの数と int `deletedfolders` - 削除されたフォルダの数を返します。

# 出力例

```
{
    "result": 0,
    "deletedfiles": 30,
    "deletedfolders": 5
}
```
