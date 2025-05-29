```
set_game(
    c::Client,
    game::AbstractString;
    type::Int=AT.GAME,
    since::Nullable{Int}=c.presence["since"],
    status::Union{PresenceStatus, AbstractString}=c.presence["status"],
    afk::Bool=c.presence["afk"],
    kwargs...,
) -> Bool
```

Shortcut for [`update_status`](@ref) to set the [`Client`](@ref)'s [`Activity`](@ref). Any additional keywords are passed into the `activity` section.
