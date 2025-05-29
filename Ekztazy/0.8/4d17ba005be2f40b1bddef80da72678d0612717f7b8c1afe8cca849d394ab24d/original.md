```
get_reactions(
    c::Client,
    channel::Integer,
    message::Integer,
    emoji::StringOrChar,
) -> Vector{User}
```

Get the [`User`](@ref)s who reacted to a [`Message`](@ref) with an [`Emoji`](@ref).
