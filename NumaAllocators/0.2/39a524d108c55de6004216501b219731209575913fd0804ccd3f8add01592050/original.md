```
NumaAllocator(node)
```

Cross-platform NUMA allocator

# Example

```jldoctest
julia> using NumaAllocators

julia> Array{UInt8}(NumaAllocator(0), 32, 32);
```
