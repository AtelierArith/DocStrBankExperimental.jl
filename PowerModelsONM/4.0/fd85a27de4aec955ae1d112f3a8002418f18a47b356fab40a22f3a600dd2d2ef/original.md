```
UnnestedGraph <: InfrastructureGraph
```

Unnested graph structure, where the attributes are

```julia
node::Vector{Pair{String,Dict{String,String}}}
edge::Vector{Dict{String,String}}
```
