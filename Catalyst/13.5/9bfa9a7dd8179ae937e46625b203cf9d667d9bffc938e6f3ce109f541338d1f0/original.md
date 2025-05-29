```
isreversible(rn::ReactionSystem)
```

Given a reaction network, returns if the network is reversible or not.

Notes:

  * Requires the `incidencemat` to already be cached in `rn` by a previous call to `reactioncomplexes`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
rcs,incidencemat = reactioncomplexes(sir)
isreversible(sir)
```
