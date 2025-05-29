```
trash_list(client::PCloudClient; kwargs...)
```

Lists the contents of a folder in the `Trash`.

The root folder of the `Trash` has `id='0'`.

Outputs the `metadata` of the folder. This metadata will have `contents` field that is array of metadatas of folder's contents.

Note that the metadata from this function has the additional field `origparentfolderid` in the metadata. This is the folder, in which the file or folder was, before it was moved to `Trash`.

So the field `parentfolderid` is showing the position in the `Trash`.

Only files and folders that belong to the current user will be outputed from this method.

Recursively listing a `Trash` folder is not an expensive operation.

This method is very simillar to `listfolder`

Source: https://docs.pcloud.com/methods/trash/trash_list.html

# Optional Arguments

  * `folderid::Int`: the id of the Trash folder. The default is 0 - the root of the Trash.
  * `nofiles::Int`: If set, then no files will be included in the Trash list - only folders.
  * `recursive::Int`: If set, then the list will be recursive - the subfolders will have their folders and files included.

# Output

On success returns the `metadata` and the `contents` of the folder from the `Trash`.

# Output Example

```
{
    result: 0,
    metadata: {
        thumb: false,
        path: "/",
        isfolder: true,
        isshared: false,
        ismine: true,
        modified: "Mon, 16 Sep 2013 12:10:32 +0000",
        created: "Mon, 16 Sep 2013 12:10:32 +0000",
        name: "/",
        folderid: 0,
        isdeleted: true,
        icon: "folder",
        id: "d0",
        contents: [
            {
                name: "Deleted folder",
                folderid: 236427,
                id: "d236427",
                origparentfolderid: 123,
                parentfolderid: 0,
                thumb: false,
                isfolder: true,
                isshared: false,
                ismine: true,
                modified: "Sat, 14 Dec 2013 13:37:33 +0000",
                created: "Tue, 03 Dec 2013 15:50:22 +0000",
                isdeleted: true,
                icon: "folder",
                contents: [ ]
            },
            {
                name: "Deleted file",
                id: "f76543",
                fileid: 76543,
                origparentfolderid: 6543,
                parentfolderid: 0,
                category: 3,
                icon: "audio",
                contenttype: "audio/x-mpegurl",
                hash: 17079372075467340000,
                size: 759,
                isfolder: false,
                thumb: false,
                isshared: false,
                modified: "Wed, 18 Sep 2013 10:18:46 +0000",
                created: "Wed, 18 Sep 2013 10:18:14 +0000",
                ismine: true,
                isdeleted: true
            }
        ]
    }
}
```
