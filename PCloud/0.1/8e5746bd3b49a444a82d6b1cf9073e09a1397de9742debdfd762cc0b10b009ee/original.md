```
listrevisions(client::PCloudClient; kwargs...)
```

Lists revisions for a given `fileid` / `path`

Source: https://docs.pcloud.com/methods/revisions/listrevisions.html

# Arguments

  * `fileid::Int`: id of the revisioned file
  * `path::String`: path the revisioned file

Use `fileid` or `path`

# Output

Lists the revisions as array, each element with the following fields:

  * `revisionid::Int`: id of the revision
  * `size::Int`: filesize of the given revision of the file
  * `hash::String`: file contents hash (same as in metadata)
  * `created::datetime`: date/time at which the revision was created

Also returns the metadata of the file.
