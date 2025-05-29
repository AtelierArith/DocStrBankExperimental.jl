```
delete_user_reaction(
    c::Client,
    channel::Integer,
    message::Integer,
    emoji::StringOrChar,
    user::Integer,
)
```

[`User`](@ref)の[`Message`](@ref)へのリアクションを削除します。
