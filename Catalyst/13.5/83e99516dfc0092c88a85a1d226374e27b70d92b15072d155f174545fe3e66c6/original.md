```
linkageclasses(rn::ReactionSystem)
```

Given the incidence graph of a reaction network, return a vector of the connected components of the graph (i.e. sub-groups of reaction complexes that are connected in the incidence graph).

Notes:

  * Requires the `incidencemat` to already be cached in `rn` by a previous call to `reactioncomplexes`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
complexes,incidencemat = reactioncomplexes(sir)
linkageclasses(sir)
```

gives

```julia
2-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
```
