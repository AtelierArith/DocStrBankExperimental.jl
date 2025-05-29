```
files_download(auth::Authorization,
               path::String
              )::Tuple{FileMetadata, Vector{UInt8}}
```

Download file `path`. Returns both its metadata and content.
