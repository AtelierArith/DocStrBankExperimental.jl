```
subnetworks(rn::ReactionSystem)
```

Find subnetworks corresponding to each linkage class of the reaction network.

Notes:

  * Requires the `incidencemat` to already be cached in `rn` by a previous call to `reactioncomplexes`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
complexes,incidencemat = reactioncomplexes(sir)
subnetworks(sir)
```
