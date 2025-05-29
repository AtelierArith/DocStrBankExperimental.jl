```
renamefolder(client::PCloudClient; kwargs...)
```

Renames (and/or moves) a folder identified by `folderid` or `path` to either `topath` (if `topath` is a existing folder to place source folder without new name for the folder it MUST end with slash - `/newpath/`) or `tofolderid`/`toname` (one or both can be provided).

Source: https://docs.pcloud.com/methods/folder/renamefolder.html

# Output

Returns `metadata` of the renamed folder.

# Output Example

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
