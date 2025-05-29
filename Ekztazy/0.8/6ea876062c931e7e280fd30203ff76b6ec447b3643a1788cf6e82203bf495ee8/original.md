```
request_guild_members(
    c::Client,
    guilds::Union{Integer, Vector{<:Integer};
    query::AbstractString="",
    limit::Int=0,
) -> Bool
```

Request offline guild members of one or more [`Guild`](@ref)s. [`on_guild_members_chunk!`](@ref) events are sent by the gateway in response. More details [here](https://discordapp.com/developers/docs/topics/gateway#request-guild-members).
