```
changeuploadlink(client::PCloudClient; kwargs...)
```

Modify upload link identified by `uploadlinkid`.

Options that, could be changed include:

Expiration date

Space of the upload link

Files of the upload link

Source: https://docs.pcloud.com/methods/upload_links/changeuploadlink.html

# Arguments

  * `uploadlinkid::Int`: id of the upload link

# Optional Arguments

  * `expire::datetime`: set expiration date of the link
  * `deleteexpire::Int`: if set, link's expiration date is removed
  * `maxspace::Int`: alter the maximum available space (in bytes) of the link
  * `maxfiles::Int`: alter the maximum available files of the link

Set `maxspace` or `maxfiles` to `0` to remove the given limit.
