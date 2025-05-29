```
save_graphml(io::IO, eng::Dict{String,<:Any}; type::String="nested")
```

Save a GraphML XML document built from `eng` network data to IO stream.

`type` controls whether the resulting graph is a NestedGraph, i.e., buses are contained within load blocks, or a UnnestedGraph, where node groups are not utilized.
