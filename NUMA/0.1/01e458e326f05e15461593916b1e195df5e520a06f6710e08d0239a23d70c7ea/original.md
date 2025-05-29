```julia
which_numa_node(ptr::Ptr{T}; variant) -> Int64

```

Query on which NUMA node the page associated with the given memory address (pointer) is located.

The optional keyword argument `variant` can be used to switch between methods used to determine the NUMA node. Valid options are `:move_pages` (default) and `:get_mempolicy`.

Note: Returned NUMA node IDs start at zero!
