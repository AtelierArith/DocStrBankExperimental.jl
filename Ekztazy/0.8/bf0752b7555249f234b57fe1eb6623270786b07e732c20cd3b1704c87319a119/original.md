```
create_reaction(c::Client, channel::Integer, message::Integer, emoji::StringOrChar)
```

React to a [`Message`](@ref). If `emoji` is a custom [`Emoji`](@ref), it should be formatted "name:id".
