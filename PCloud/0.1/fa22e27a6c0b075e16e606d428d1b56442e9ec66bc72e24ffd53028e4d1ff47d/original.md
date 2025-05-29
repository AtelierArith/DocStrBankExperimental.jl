```
copytolink(client::PCloudClient; kwargs...)
```

Copy a file from the current user's filesystem to a upload link.

Source: https://docs.pcloud.com/methods/upload_links/copytolink.html

# Arguments

  * `code::String`: code of the upload link
  * `fileid::Int`: id of the copied file
  * `path::String`: path the copied file

Use "fileid" or "path"

# Optional Arguments

toname "string" the name to save the copied file. If it is not provided, then the name of the file is used.
