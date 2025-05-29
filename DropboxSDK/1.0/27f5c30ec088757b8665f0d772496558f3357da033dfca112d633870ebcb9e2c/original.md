```
files_upload(auth::Authorization,
             upload_spec_channel::Union{AbstractChannel{UploadSpec},
                                        AbstractVector{UploadSpec}}
            )::Vector{FileMetadata}
```

Uploading several files simultaneously in an efficient manner. The upload spec channel is used to describe the uploaded files. This channel needs to be closed after passing in all upload specs to finalize the uploads. The return value is then a vector of all metadata of the uploaded files.

This function is efficient if many files are uploaded.
