```
renamefile(client::PCloudClient; kwargs...)
```

Rename a file

Renames (and/or moves) a file identified by `fileid` or `path` to either `topath` (if `topath` is a foldername without new filename it MUST end with slash - /newpath/) or `tofolderid`/`toname` (one or both can be provided).

If the destination file already exists it will be replaced atomically with the source file, in this case the metadata will include `deletedfileid` with the fileid of the old file at the destination, and the source and destination files revisions will be merged together.

Source: https://docs.pcloud.com/methods/file/renamefile.html

# Arguments

  * `fileid::Int`: ID of the renamed file
  * `path::String`: Path to the renamed file
  * `topath::String`: Destination path of renamed file
  * `tofolderid::Int`: Id of the folder to which the file is moved
  * `toname::String`: Destination filename of the renamed file

Use fileid or path

# Output

On success returns renamed file's `metadata` with `deletedfileid` if merged file.

# Output Example

```
{
    "result": 0,
    "metadata": {
        "id": "f1729212",
        "fileid": 1729212,
        "size": 73269,
        "isfolder": false,
        "hash": 10681749967730527559,
        "isshared": false,
        "thumb": true,
        "height": 600,
        "contenttype": "image/jpeg",
        "icon": "image",
        "created": "Wed, 02 Oct 2013 14:29:11 +0000",
        "width": 900,
        "modified": "Wed, 02 Oct 2013 16:07:40 +0000",
        "ismine": true,
        "name": "My picture.jpg",
        "category": 1,
        "parentfolderid": 0
    }
}
```
