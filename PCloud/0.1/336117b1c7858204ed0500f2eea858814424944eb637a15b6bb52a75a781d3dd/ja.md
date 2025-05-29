```
renamefolder(client::PCloudClient; kwargs...)
```

`folderid` または `path` で識別されるフォルダーの名前を変更（および/または移動）します。`topath` が既存のフォルダーで、ソースフォルダーの新しい名前なしで配置する場合は、スラッシュで終わる必要があります - `/newpath/` または `tofolderid`/`toname`（どちらか一方または両方を提供できます）。

Source: https://docs.pcloud.com/methods/folder/renamefolder.html

# 出力

名前が変更されたフォルダーの `metadata` を返します。

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
