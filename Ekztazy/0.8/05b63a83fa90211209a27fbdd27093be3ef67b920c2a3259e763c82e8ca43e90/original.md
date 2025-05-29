```
upload_file(c::Client, ch::DiscordChannel, path::AbstractString; kwargs...) -> Message
```

Send a [`Message`](@ref) with a file [`Attachment`](@ref). Any keywords are passed on to [`create_message`](@ref).
