```
isweaklyreversible(rn::ReactionSystem, subnetworks)
```

Determine if the reaction network with the given subnetworks is weakly reversible or not.

Notes:

  * Requires the `incidencemat` to already be cached in `rn` by a previous call to `reactioncomplexes`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
rcs,incidencemat = reactioncomplexes(sir)
subnets = subnetworks(rn)
isweaklyreversible(rn, subnets)
```
