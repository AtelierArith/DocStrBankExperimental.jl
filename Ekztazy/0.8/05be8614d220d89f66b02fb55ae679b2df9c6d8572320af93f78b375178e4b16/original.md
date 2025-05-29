```
delete_user_reaction(
    c::Client,
    channel::Integer,
    message::Integer,
    emoji::StringOrChar,
    user::Integer,
)
```

Delete a [`User`](@ref)'s reaction to a [`Message`](@ref).
