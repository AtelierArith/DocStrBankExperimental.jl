```
files_upload(auth::Authorization,
             path::String,
             content_channel::Channel{Vector{UInt8}}
            )::FileMetadata
```

Upload a file `path`. The upload channel is used to pass in the data in chunks, where each chunk should be no larger than 150 MByte. This channel needs to be closed after passing in all chunks to finalize the upload. The return value is then the metadata of the uploaded file.

This function should only be used if only a few files are to be uploaded. Other `files_upload` functions are more efficient if there are many files to be uploaded.
