```
upload_file(c::Client, ch::DiscordChannel, path::AbstractString; kwargs...) -> Message
```

ファイル [`Attachment`](@ref) を含む [`Message`](@ref) を送信します。任意のキーワードは [`create_message`](@ref) に渡されます。
