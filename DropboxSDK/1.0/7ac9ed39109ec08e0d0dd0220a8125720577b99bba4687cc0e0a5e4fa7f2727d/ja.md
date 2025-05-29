```
struct UploadSpec
    destination::String
    content_channel::Union{AbstractChannel{Vector{UInt8}},
                           AbstractVector{Vector{UInt8}}}
end
```

アップロードするファイルのパスとコンテンツの両方を指定します。コンテンツはチャネルを介してチャンクとして渡す必要があります。
