```
ZipArchive
```

Type describing zip archive for reading and writing.

## Fields

  * `archive_ptr::Ptr{LibZipT}`: The pointer to the C library zip structure.
  * `source_ptr::Ptr{LibZipSourceT}`: The pointer to the C library source structure.
  * `comment::String`: The archive's comment.
  * `source_data::Vector{Vector{UInt8}}`: A container to hold in-memory source data buffers for the archive.
  * `closed::Bool`: Flag indicating whether the archive is closed.
