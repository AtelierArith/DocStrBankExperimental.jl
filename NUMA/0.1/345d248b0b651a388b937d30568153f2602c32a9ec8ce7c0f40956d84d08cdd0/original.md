```julia
numa_node_size(

) -> @NamedTuple{memtot::Int64, memfree::Int64}
numa_node_size(
    node::Integer
) -> @NamedTuple{memtot::Int64, memfree::Int64}

```

Returns a named tuple holding the total memory and free memory of the given NUMA node. If no node index is provided as an argument, `current_numa_node()` is used.
