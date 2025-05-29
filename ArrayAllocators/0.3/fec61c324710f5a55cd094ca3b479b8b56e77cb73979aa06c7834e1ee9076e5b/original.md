```
calloc
```

[`CallocAllocator`](@ref) singleton instance. `calloc` will allocate memory and guarantee initialization to `0`. See the type for details and the [C standard library function](https://en.cppreference.com/w/c/memory/calloc) for further details.

# Example

```jldoctest
julia> A = Array{UInt8}(calloc, 16, 16);

julia> sum(A)
0x0000000000000000
```
