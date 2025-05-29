```
encode(e, src::AbstractVector{UInt8})::Vector{UInt8}
```

Encode the input vector `src` using encoder `e`. `e` must implement [`decoded_size_range`](@ref), [`encode_bound`](@ref), and [`try_encode!`](@ref).

Throw an error if `length(src)` is not in `decoded_size_range(e)`

Otherwise throw an error.

See also [`EncodeOptions`](@ref) and [`decode`](@ref).
