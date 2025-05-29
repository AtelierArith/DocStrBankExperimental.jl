```
unsafe_parse_gzip_header(
    in_ptr::Ptr, max_len::Integer,
    extra_data::Union{Vector{GzipExtraField}, Nothing}=nothing
)
```

Parse the input data, returning a `GzipHeader` object, or a `LibDeflateError`. The parser will not read more than `max_len` bytes. If a vector of gzip extra data is passed, it will not allocate a new vector, but overwrite the given one.
