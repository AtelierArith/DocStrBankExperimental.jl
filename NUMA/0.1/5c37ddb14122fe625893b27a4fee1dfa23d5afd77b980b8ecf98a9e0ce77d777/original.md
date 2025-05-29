```julia
which_numa_node(arr::AbstractArray; ...) -> Int64
which_numa_node(arr::AbstractArray, i; kwargs...) -> Int64

```

Query on which NUMA node the given array is allocated (assuming that it is allocated on a single node).

Technically only the address of a single element is checked (by default the first one). The optional second integer argument can be used to specify this element.

The optional keyword argument `variant` can be used to switch between methods used to determine the NUMA node. Valid options are `:move_pages` (default) and `:get_mempolicy`.

Note: Returned NUMA node IDs start at zero!
