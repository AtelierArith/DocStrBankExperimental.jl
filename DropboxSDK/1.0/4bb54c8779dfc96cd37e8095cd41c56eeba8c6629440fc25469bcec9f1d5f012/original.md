```
files_upload(auth::Authorization,
             path::String,
             content::Vector{UInt8}
            )::FileMetadata
```

Upload the byte array `content` to a file `path`, returning its metadata. This function should only be used for small files (< 150 MByte), and if only a few files are uploaded. Other `files_upload` functions are more efficient for large files and/or if there are many files to be uploaded.
