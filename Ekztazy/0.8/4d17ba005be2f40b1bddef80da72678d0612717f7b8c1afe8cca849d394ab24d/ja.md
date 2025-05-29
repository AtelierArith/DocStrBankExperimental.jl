```
get_reactions(
    c::Client,
    channel::Integer,
    message::Integer,
    emoji::StringOrChar,
) -> Vector{User}
```

[`Emoji`](@ref)で反応した[`Message`](@ref)の[`User`](@ref)を取得します。
