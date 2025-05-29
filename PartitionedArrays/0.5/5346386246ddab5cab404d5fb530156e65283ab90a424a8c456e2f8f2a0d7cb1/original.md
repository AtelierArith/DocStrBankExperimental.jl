```
assembly_graph(index_partition;kwargs...)
```

Return an instance of [`ExchangeGraph`](@ref) representing the communication graph needed to perform assembly of distributed vectors defined on the index partition `index_partition`. `kwargs` are delegated to [`ExchangeGraph`](@ref) in order to find the receiving neighbors from the sending ones.

Equivalent to

```
neighbors = assembly_neighbors(index_partition;kwargs...)
ExchangeGraph(neighbors...)
```
