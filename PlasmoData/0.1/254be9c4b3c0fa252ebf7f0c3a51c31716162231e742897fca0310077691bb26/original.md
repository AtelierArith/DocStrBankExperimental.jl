```
get_ordered_edge_data(dg::D, attribute::String) where {D <: DataGraphUnion}
```

Returns the ordered edge data vector for `attribute`. For `DataGraph`s, this means all edges connected to `dg.nodes[1]` are ordered first, and so on. For `DataDiGraph`s, this means that all edges originating at `dg.nodes[1]`  are ordered first, and so on for `length(dg.nodes)`
