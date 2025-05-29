```
create_reaction(c::Client, channel::Integer, message::Integer, emoji::StringOrChar)
```

[`Message`](@ref)にリアクションを追加します。`emoji`がカスタム[`Emoji`](@ref)の場合、"name:id"の形式で指定する必要があります。
