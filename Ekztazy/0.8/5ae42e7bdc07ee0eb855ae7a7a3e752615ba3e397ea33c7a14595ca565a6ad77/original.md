```
update_status(
    c::Client,
    since::Nullable{Int},
    activity::Nullable{Activity},
    status::Union{PresenceStatus, AbstractString},
    afk::Bool,
) -> Bool
```

Indicate a presence or status update. A `PresenceUpdate` event is sent by the gateway in response. More details [here](https://discordapp.com/developers/docs/topics/gateway#update-status).
