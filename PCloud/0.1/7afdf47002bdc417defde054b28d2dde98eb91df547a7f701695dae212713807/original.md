```
deletefolderrecursive(client::PCloudClient; kwargs...)
```

Deletes a folder

Expects either `path` string parameter (discouraged) or int `folderid` parameter.

*Note:* This function deletes files, directories, and removes sharing. Use with extreme care.

Source: https://docs.pcloud.com/methods/folder/deletefolderrecursive.html

# Arguments

  * `path::String`: path to the folder (discouraged)
  * `folderid::Int`: id of the folder

# Output

Upon success returns int `deletedfiles` - the number of deleted files and int `deletedfolders` - number of deleted folders.

# Output Example

```
{
    "result": 0,
    "deletedfiles": 30,
    "deletedfolders": 5
}
```
