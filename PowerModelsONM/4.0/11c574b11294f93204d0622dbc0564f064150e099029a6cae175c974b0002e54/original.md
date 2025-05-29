```
NestedGraph <: InfrastructureGraph
```

Nested Graph structure, where the attributes are

```julia
node::Dict{String,UnnestedGraph}
edge::Vector{Dict{String,String}}
```
