```
NumaAllocators
```

Extends `ArrayAllocators` to allocate memory on specific NUMA nodes.

# Examples

```julia
using NumaAllocators

Array{UInt8}(numa(0), 100)
Array{UInt8}(NumaAllocator(1), 100)
```
