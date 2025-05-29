```
copyfolder(client::PCloudClient; kwargs...)
```

`folderid` または `path` で識別されるフォルダーを `topath` または `tofolderid` にコピーします。

ソース: https://docs.pcloud.com/methods/folder/copyfolder.html

# 引数

  * `folderid::Int`: ソースフォルダーのID
  * `path::String`: ソースフォルダーのパス
  * `tofolderid::Int`: 宛先フォルダーのID
  * `topath::String`: 宛先パス

# オプション引数

  * `noover::Int`: 設定されている場合、同じ名前のファイルが既に存在する場合は上書きが行われず、エラー2004が返されます
  * `skipexisting::Int`: 設定されている場合、既に存在するファイルはスキップされます
  * `copycontentonly::Int`: 設定されている場合、ソースフォルダーの内容のみがコピーされ、それ以外の場合はフォルダー自体がコピーされます

# 出力

作成されたフォルダーの `metadata` を返します。

# 出力例

```
{
    "result": 0,
    "metadata": {
        "parentfolderid": 0,
        "id": "d230807",
        "modified": "Wed, 02 Oct 2013 13:23:35 +0000",
        "thumb": false,
        "created": "Wed, 02 Oct 2013 13:11:53 +0000",
        "folderid": 230807,
        "ismine": true,
        "isshared": false,
        "isfolder": true,
        "name": "Simple Folder",
        "icon": "folder"
    }
}
```
