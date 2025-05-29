```
incidencematgraph(rn::ReactionSystem)
```

Construct a directed simple graph where nodes correspond to reaction complexes and directed edges to reactions converting between two complexes.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
incidencematgraph(sir)
```
