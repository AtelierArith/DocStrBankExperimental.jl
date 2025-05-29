```
request_guild_members(
    c::Client,
    guilds::Union{Integer, Vector{<:Integer};
    query::AbstractString="",
    limit::Int=0,
) -> Bool
```

1つ以上の[`Guild`](@ref)のオフラインギルドメンバーをリクエストします。[`on_guild_members_chunk!`](@ref)イベントは、ゲートウェイによって応答として送信されます。詳細は[こちら](https://discordapp.com/developers/docs/topics/gateway#request-guild-members)を参照してください。
