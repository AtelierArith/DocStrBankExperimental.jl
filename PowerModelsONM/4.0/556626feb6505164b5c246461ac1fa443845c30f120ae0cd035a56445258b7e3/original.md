```
build_graphml_document(eng::Dict{String,<:Any}; type::Type="nested")
```

Helper function to build GraphML XML document from a `eng` network data structure.

`type` controls whether the resulting graph is a NestedGraph, i.e., buses are contained within load blocks, or a UnnestedGraph, where node groups are not utilized.
