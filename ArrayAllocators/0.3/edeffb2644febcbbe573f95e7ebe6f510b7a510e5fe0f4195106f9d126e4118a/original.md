```
malloc
```

[`MallocAllocator`](@ref) singleton instance. `malloc` will only allocate memory. It does not initialize memory is is similar in use as `undef`. See the type and the [C standard library function](https://en.cppreference.com/w/c/memory/malloc) for details.

# Example

```jldoctest
julia> Array{UInt8}(malloc, 16, 16);

```
