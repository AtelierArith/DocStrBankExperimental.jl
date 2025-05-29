```
copyfolder(client::PCloudClient; kwargs...)
```

Copies a folder identified by `folderid` or `path` to either `topath` or `tofolderid`.

Source: https://docs.pcloud.com/methods/folder/copyfolder.html

# Arguments

  * `folderid::Int`: id of the source folder
  * `path::String`: path of the source folder
  * `tofolderid::Int`: id of destination folder
  * `topath::String`: destination path

# Optional Arguments

  * `noover::Int`: If it is set and files with the same name already exist, no overwriting will be preformed and error 2004 will be returned
  * `skipexisting::Int`: If set will skip files that already exist
  * `copycontentonly::Int`: If it is set only the content of source folder will be copied otherwise the folder itself is copied

# Output

Returns `metadata` of the created folder.

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
