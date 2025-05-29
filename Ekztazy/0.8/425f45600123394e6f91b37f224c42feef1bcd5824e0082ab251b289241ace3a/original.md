```
plaintext(m::Message) -> String
plaintext(c::Client, m::Message) -> String
```

Get the [`Message`](@ref) contents with any [`User`](@ref) mentions replaced with their plaintext. If a [`Client`](@ref) is provided, [`DiscordChannel`](@ref)s [`Role`](@ref) are also replaced. However, only channels and roles stored in state are replaced; no API requests are made.
