```
copyfile(client::PCloudClient; kwargs...)
```

Takes one file and copies it as another file in the user's filesystem.

Expects `fileid` or `path` to identify the source file and `tofolderid`+`toname` or `topath` to identify destination filename.

If `toname` is ommited, original filename is used.

The same is true if the last character of `topath` is '/' (slash), thus identifying only the target folder. The target file will be separate, newly created (with current creation time unless old file is overwritten) independent file.

Any future operations on either the source or destination file will not modify the other one.

This call is useful when you want to create a public link from somebody else's file (shared with you).

Source: https://docs.pcloud.com/methods/file/copyfile.html

# Arguments

  * `fileid::Int`: id of the target file
  * `path::String`: path to the target file
  * `tofolderid::Int`: id of destination folder
  * `topath::String`: destination path

Note that not all are required at single method call

# Optional Arguments

  * `toname::String`: name of the destination file. If omitted, then the original filename is used
  * `noover::Int`: If it is set and file with the specified name already exists, no overwriting will be preformed
  * `mtime::Int`: if set, file modified time is set. Have to be unix time seconds.
  * `ctime::Int`: if set, file created time is set. It's required to provide mtime to set ctime. Have to be unix time seconds.

# Output

Upon success returns metadata of the destination file ( the copy result ).

# Output Example

```
{
    "result": 0,
    "metadata": {
        "category": 1,
        "width": 900,
        "thumb": true,
        "created": "Wed, 02 Oct 2013 15:05:17 +0000",
        "hash": 10681749967730527559,
        "icon": "image",
        "ismine": true,
        "name": "Simple image.jpg",
        "modified": "Wed, 02 Oct 2013 15:05:17 +0000",
        "isfolder": false,
        "contenttype": "image/jpeg",
        "fileid": 1732283,
        "isshared": false,
        "id": "f1732283",
        "size": 73269,
        "parentfolderid": 28110,
        "height": 600
    }
}
```
