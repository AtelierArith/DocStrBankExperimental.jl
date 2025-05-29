```
linkageclasses(rn::ReactionSystem)
```

Given the incidence graph of a reaction network, return a vector of the connected components of the graph (i.e. sub-groups of reaction complexes that are connected in the incidence graph).

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
linkageclasses(sir)
```

gives

```julia
2-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
```
