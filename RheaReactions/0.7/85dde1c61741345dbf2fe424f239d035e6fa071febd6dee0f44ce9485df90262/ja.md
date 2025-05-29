```julia
get_reactions(
    rids;
    verbose
) -> Union{Nothing, Vector{RheaReactions.RheaReaction}}

```

[`RheaReaction`](@ref)のベクターを返します。代謝物を暗黙的にキャッシュします。
