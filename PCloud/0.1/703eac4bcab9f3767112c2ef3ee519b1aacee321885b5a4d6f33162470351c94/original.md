```
trash_restore(client::PCloudClient; kwargs...)
```

Restores files or folders from the `Trash` back to the filesystem.

The destination, where the data will be restored can be automatically calculated via trash_restorepath or it could be specified by the user (use `restoreto` parameter).

If `folderid='0'`, then all data in the `Trash` will be restored, as close to their original positions, as possible. If `restoreto` is set, then all data in the `Trash` will be placed into this folder.

If the destination is a shared folder, then a user to which the folder was shared, will need CREATE access to the folder.

If the current user used space + the resotred files size is greater than the user quota, then this method will restore, until the first file that goes over quota is restored. Then it will raise an error.

Source: https://docs.pcloud.com/methods/trash/trash_restore.html

# Arguments

  * `fileid::Int`: file id of the restored file
  * `folderid::Int`: folder id of the restored folder

Use `fileid` or `folderid`

# Optional Arguments

  * `restoreto::Int`: If given, then this folder will be chosen as a destination of the restored data.
  * `metadata::Int`: If set and restoring a folder, then the metadata of the folder will have contents filled with the information about files and folders in the restired folder.

# Output

On success returns the `metadata` of the restored file or folder.

If the root of the trash is restored and `restoreto` is specified, then the metadata is shown for the `restoreto` folder.

Else if `restoreto` is not specified, then result is a list `restored` of `metadatas` of the restored files / folders.

# Output Example

```
{
    result: 0,
    metadata: {
        name: "Deleted folder",
        folderid: 236427,
        id: "d236427",
        parentfolderid: 0,
        thumb: false,
        isfolder: true,
        isshared: false,
        ismine: true,
        modified: "Sat, 16 Dec 2013 16:20:00 +0000",
        created: "Tue, 03 Dec 2013 15:50:22 +0000",
        isdeleted: false,
        icon: "folder",
        contents: [
        ]
    }
}
```
