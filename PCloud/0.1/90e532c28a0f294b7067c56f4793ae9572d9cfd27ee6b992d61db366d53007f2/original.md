```
deletefile(client::PCloudClient; kwargs...)
```

Delete a file identified by `fileid` or `path`.

Source: https://docs.pcloud.com/methods/file/deletefile.html

# Arguments

  * `fileid::Int`: ID of the deleted file
  * `path::String`: Path to the deleted file

Use fileid or path

# Output

On success returns file's `metadata` with `isdeleted` set.

# Output Example

```
{
    "result": 0,
    "id": "139-0",
    "metadata": {
        "isfolder": false,
        "icon": "image",
        "size": 15604,
        "name": "Simple image.jpg",
        "category": 1,
        "contenttype": "image/jpeg",
        "parentfolderid": 0,
        "isdeleted": true,
        "hash": 6306013028049022731,
        "ismine": true,
        "isshared": false,
        "id": "f1736716",
        "height": 300,
        "width": 222,
        "modified": "Wed, 02 Oct 2013 16:00:40 +0000",
        "thumb": true,
        "created": "Wed, 02 Oct 2013 15:57:13 +0000",
        "fileid": 1736716
    }
}
```
