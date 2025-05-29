```
uploadlinkprogress(client::PCloudClient; kwargs...)
```

Monitor the progress of uploaded files.

Source: https://docs.pcloud.com/methods/upload_links/uploadlinkprogress.html

# Arguments

  * `code::String`: code of the upload link
  * `progresshash::String`: hash for monitoring passed to uploadtolink

# Output

Returns same data as uploadprogress but without `files`.
