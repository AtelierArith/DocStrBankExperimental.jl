```
order_edges!(dg) where {D <: DataGraphUnion}
```

Arranges in place the edges of `dg` so that they follow the order of `dg.nodes`. For `DataGraph`s, this means all edges connected to `dg.nodes[1]` are ordered first, and so on. For `DataDiGraph`s, this means that all edges originating at `dg.nodes[1]` are ordered first, and so on for `length(dg.nodes)`
