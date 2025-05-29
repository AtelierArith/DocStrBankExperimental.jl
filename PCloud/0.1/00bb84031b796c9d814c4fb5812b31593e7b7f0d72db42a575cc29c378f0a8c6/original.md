```
revertrevision(client::PCloudClient; kwargs...)
```

Takes `fileid`/`path` and `revisionid` as parameters and reverts the file to a given revision.

Current file contents are saved as new revision.

Source: https://docs.pcloud.com/methods/revisions/revertrevision.html

# Arguments

  * `fileid::Int`: id of the reverted file
  * `path::String`: path the reverted file
  * `revisionid::Int`: id of the revistion, to which the file is reverted

Use `fileid` or `path`

# Output

On success returns new metadata of the file.
