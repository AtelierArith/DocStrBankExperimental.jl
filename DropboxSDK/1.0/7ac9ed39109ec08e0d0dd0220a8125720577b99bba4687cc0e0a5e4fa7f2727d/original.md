```
struct UploadSpec
    destination::String
    content_channel::Union{AbstractChannel{Vector{UInt8}},
                           AbstractVector{Vector{UInt8}}}
end
```

Specify both path and content for a file that is to be uploaded. The content needs to be passed in as chunks via a channel.
