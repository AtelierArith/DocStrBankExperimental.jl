```
incidencematgraph(rn::ReactionSystem)
```

Construct a directed simple graph where nodes correspond to reaction complexes and directed edges to reactions converting between two complexes.

Notes:

  * Requires the `incidencemat` to already be cached in `rn` by a previous call to `reactioncomplexes`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
complexes,incidencemat = reactioncomplexes(sir)
incidencematgraph(sir)
```
