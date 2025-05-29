```julia
numa_node_of_cpu() -> Int64
numa_node_of_cpu(cpuid::Integer) -> Int64

```

Returns the NUMA node that the cpu with the given id (starting at zero) belongs to.
