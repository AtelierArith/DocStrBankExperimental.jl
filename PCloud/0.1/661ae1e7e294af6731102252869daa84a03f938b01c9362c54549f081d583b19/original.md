```
trash_clear(client::PCloudClient; kwargs...)
```

Deletes

*permanently* files or folders from the `Trash`.

Files and folders deleted via this method cannot be restored.

If `folderid='0'`, then all data from the `Trash` will be removed.

Source: https://docs.pcloud.com/methods/trash/trash_clear.html

# Arguments

  * `fileid::Int`: file id of the file that is removed from Trash
  * `folderid::Int`: folder id of the folder that is removed from Trash

Use `fileid` or `folderid`

# Output Example

```
{
    "result": 0
}
```
