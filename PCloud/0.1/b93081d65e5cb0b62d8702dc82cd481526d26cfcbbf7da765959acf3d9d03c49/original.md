```
createfolder(client::PCloudClient; kwargs...)
```

Creates a folder.

Expects either `path` string parameter (discouraged) or int `folderid` and string `name` parameters.

Source: https://docs.pcloud.com/methods/folder/createfolder.html

# Arguments

  * `path::String`: path to the folder(discouraged)
  * `folderid::Int`: id of the folder
  * `name::String`: name of the folder

Use `path` or `folderid` + `name`

# Output

Upon success returns `metadata` structure.

# Output Example

```
{
    "result": 0,
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
