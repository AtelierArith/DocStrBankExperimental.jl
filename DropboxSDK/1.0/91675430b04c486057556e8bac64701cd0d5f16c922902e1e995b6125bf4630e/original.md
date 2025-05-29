```
calc_content_hash(
    data_channel::Union{AbstractChannel{<: AbstractVector{UInt8}},
                        AbstractVector{<: AbstractVector{UInt8}}}
)::String
```

Calculate a content hash with Dropbox's algorithm from chunks of data. The data channel is used to pass in the data in chunks. The result is returned once the data channel is closed.
