```
linkagedeficiencies(network::ReactionSystem)
```

Calculates the deficiency of each sub-reaction network within `network`.

Notes:

  * Requires the `incidencemat` to already be cached in `rn` by a previous call to `reactioncomplexes`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
rcs,incidencemat = reactioncomplexes(sir)
linkage_deficiencies = linkagedeficiencies(sir)
```
