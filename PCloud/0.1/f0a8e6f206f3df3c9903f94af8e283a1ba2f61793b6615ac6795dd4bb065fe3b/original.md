```
trash_restorepath(client::PCloudClient; kwargs...)
```

For a desired file or folder from the `Trash`, calculates where to restore.

This method is granted that will choose such the destination folder, that `ismine` is `true`.

If the parent folder is also deleted, then this method will calculate the path by going to the parent of the folder. That way the file or folder will be restored at most at the root of the file system.

Also, if there are some name conflicts, then a new name will be generated, that is `Name (k)` , if there are `k-1` files with the same name.

Source: https://docs.pcloud.com/methods/trash/trash_restorepath.html

# Arguments

  * `fileid::Int`: file id of the file that would be restored
  * `folderid::Int`: folder id of the folder that would be restored

Use `fileid` or `folderid`

# Output

On success returns the follwing `metadatas`

  * `metadata`: Information how the file or folder will look after restoring
  * `destination`: Information about the calculated destination of the restored foldre

# Output Example

```
{
    result: 0,
    metadata: {
        name: "Deleted folder",
        id: "d56986",
        folderid: 56986,
        parentfolderid: 56980,
        isdeleted: true,
        ismine: true,
        icon: "folder",
        created: "Mon, 03 Feb 2014 15:02:56 +0000",
        modified: "Mon, 03 Feb 2014 15:03:13 +0000",
        isfolder: true,
        thumb: false,
        isshared: true
    },
    destination: {
        name: "The destination folder",
        id: "d56980",
        folderid: 56980,
        parentfolderid: 0,
        ismine: true,
        icon: "folder",
        created: "Fri, 31 Jan 2014 12:57:56 +0000",
        modified: "Mon, 03 Feb 2014 15:04:32 +0000",
        isfolder: true,
        thumb: false,
        isshared: true
    }
}
```
