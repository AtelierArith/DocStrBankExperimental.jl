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

[`update_status`](@ref) のショートカットで、[`Client`](@ref) の [`Activity`](@ref) を設定します。追加のキーワードは `activity` セクションに渡されます。
