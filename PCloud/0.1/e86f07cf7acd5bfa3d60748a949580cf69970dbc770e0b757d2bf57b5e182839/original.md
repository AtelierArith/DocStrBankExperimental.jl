```
listfolder(client::PCloudClient; kwargs...)
```

Receive data for a folder.

Expects folderid or path parameter, returns folder's `metadata`. The metadata will have `contents` field that is array of metadatas of folder's contents.

Recursively listing the root folder is not an expensive operation.

Source: https://docs.pcloud.com/methods/folder/listfolder.html

# Arguments

  * `path::String`: path to the folder(discouraged)
  * `folderid::Int`: id of the folder

Use `path` or `folderid`

# Optional Arguments

  * `recursive::Int`: If is set full directory tree will be returned, which means that all directories will have contents filed.
  * `showdeleted::Int`: If is set, deleted files and folders that can be undeleted will be displayed.
  * `nofiles::Int`: If is set, only the folder (sub)structure will be returned.
  * `noshares::Int`: If is set, only user's own folders and files will be displayed.

# Output

Returns folder's `metadata`. The metadata will have `contents` field that is array of metadatas of folder's contents.

# Output Example

```
{
    result: 0,
    metadata: {
        icon: "folder",
        id: "d0",
        modified: "Thu, 19 Sep 2013 07:31:46 +0000",
        path: "/",
        thumb: false,
        created: "Thu, 19 Sep 2013 07:31:46 +0000",
        folderid: 0,
        isshared: false,
        isfolder: true,
        ismine: true,
        name: "/",
        contents: [
            {
                parentfolderid: 0,
                id: "d230807",
                modified: "Wed, 02 Oct 2013 13:23:35 +0000",
                path: "/Simple Folder",
                thumb: false,
                created: "Wed, 02 Oct 2013 13:11:53 +0000",
                folderid: 230807,
                ismine: true,
                isshared: false,
                isfolder: true,
                name: "Simple Folder",
                icon: "folder"
            }, {
                icon: "audio",
                contenttype: "audio/mpeg",
                parentfolderid: 0,
                modified: "Wed, 02 Oct 2013 13:23:19 +0000",
                path: "/Simple Audio.mp3",
                hash: 5380817599554757000,
                thumb: false,
                created: "Wed, 02 Oct 2013 13:23:19 +0000",
                id: "f1723778",
                ismine: true,
                category: 3,
                fileid: 1723778,
                isshared: false,
                isfolder: false,
                name: "Simple Audio.mp3",
                size: 11252576
            }]
    }
}
```
