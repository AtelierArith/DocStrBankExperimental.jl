```
numa(node)
```

Create a `NumaAllocator` on NUMA node `node`. Short hand for [`NumaAllocator`](@ref) constructor.

# Example

```jldoctest
julia> using NumaAllocators

julia> Array{UInt8}(numa(0), 32, 32);
```
