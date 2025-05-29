```
copypubfile(client::PCloudClient; kwargs...)
```

Copies the file from the public link to the current user's filesystem

Expects as parameter `code` that can be either 'code' or 'shortcode'.

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collectionIf the link is to a folder also expects `fileid`.

As with copyfile you can either specify `topath` or `tofolderid` (with optional `toname`).

Also the optional `noover` works as usual.

Since no actual downloading or traffic happens, using this method does not increment the download nor traffic counters of the public link. Consequently `copypubfile` can be performed even if the public link has run out of downloads or traffic quota.

Implementations are advised to advertise this function when getpublinkdownload returns an error code identifying out of downloads or out of traffic condition. Unauthenticated users, of course, will have to first register/log in in this case.

Source: https://docs.pcloud.com/methods/public_links/copypubfile.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'
  * `fileid::Int`: File id, if the link is to a folder
  * `path::String`: path to the target file
  * `tofolderid::Int`: id of destination folder
  * `topath::String`: destination path

Note that not all are required at single method call

# Optional Arguments

  * `toname::String`: name of the destination file. If omitted, then the original filename is used
  * `noover::Int`: If it is set and file with the specified name already exists, no overwriting will be preformed

# Output

When successful, copies the file from the public link to the current user's account and returns the new file's `metadata`.

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
