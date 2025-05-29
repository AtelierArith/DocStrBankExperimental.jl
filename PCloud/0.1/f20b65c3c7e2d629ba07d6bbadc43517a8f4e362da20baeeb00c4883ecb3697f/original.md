```
pcloud_stat(client::PCloudClient; kwargs...)
```

The `stat` API method returns information about the file pointed to by `fileid` or `path`. It's is recomended to use `fileid`.

Source: https://docs.pcloud.com/methods/file/stat.html

# Arguments

  * `path::String`: path to the file (discouraged)
  * `fileid::Int`: id of the file

# Output

Returns metadata.

# Output Example

```
{
    "result": 0,
    "metadata": {
      "ismine": true,
      "id": "f1729212",
      "created": "Wed, 02 Oct 2013 14:29:11 +0000",
      "modified": "Wed, 02 Oct 2013 14:29:11 +0000",
      "hash": 10681749967730527559,
      "isshared": false,
      "isfolder": false,
      "category": 1,
      "parentfolderid": 0,
      "icon": "image",
      "fileid": 1729212,
      "height": 600,
      "width": 900,
      "path": "/Simple image.jpg",
      "name": "Simple image.jpg",
      "contenttype": "image/jpeg",
      "size": 73269,
      "thumb": true
    }
}

```
