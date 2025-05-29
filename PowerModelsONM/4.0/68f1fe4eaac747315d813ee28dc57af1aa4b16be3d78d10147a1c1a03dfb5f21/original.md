```
save_graphml(graphml_file::String, eng::Dict{String,<:Any}; type::String="nested")
```

Save a GraphML XML document built from `eng` network data to `graphml_file`.

`type` controls whether the resulting graph is a NestedGraph, i.e., buses are contained within load blocks, or a UnnestedGraph, where node groups are not utilized.
