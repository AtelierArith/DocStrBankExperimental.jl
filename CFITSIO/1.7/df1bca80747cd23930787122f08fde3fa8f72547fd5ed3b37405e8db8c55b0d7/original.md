```
fits_write_key(f::FITSFile, keyname::String, value, comment::Union{String, Nothing} = nothing)
```

Write a keyword of the appropriate data type into the CHU. If `comment` is `nothing`, the keyword is written without a comment.
