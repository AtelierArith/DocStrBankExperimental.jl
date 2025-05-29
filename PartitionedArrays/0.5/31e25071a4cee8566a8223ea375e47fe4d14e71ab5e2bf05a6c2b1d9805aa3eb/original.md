```
neigs_snd, neigs_rcv = assembly_neighbors(index_partition;kwargs...)
```

Return the ids of the neighbor parts from we send and receive data respectively in the assembly of distributed vectors defined on the index partition `index_partition`. partition `index_partition`. `kwargs` are delegated to [`ExchangeGraph`](@ref) in order to find the receiving neighbors from the sending ones.
