```julia
get_reactions(
    rids;
    verbose
) -> Union{Nothing, Vector{RheaReactions.RheaReaction}}

```

Return a vector of [`RheaReaction`](@ref)s. Implicitly cache metabolites.
