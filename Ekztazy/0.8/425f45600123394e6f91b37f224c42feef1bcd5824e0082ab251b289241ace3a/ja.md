```
plaintext(m::Message) -> String
plaintext(c::Client, m::Message) -> String
```

[`User`](@ref) メンションをプレーンテキストに置き換えた [`Message`](@ref) の内容を取得します。`[`Client`](@ref)` が提供されている場合、[`DiscordChannel`](@ref) の [`Role`](@ref) も置き換えられます。ただし、状態に保存されているチャンネルとロールのみが置き換えられ、API リクエストは行われません。
