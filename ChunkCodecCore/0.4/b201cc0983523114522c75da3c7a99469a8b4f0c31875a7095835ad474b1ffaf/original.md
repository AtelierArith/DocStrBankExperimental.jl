```
try_encode!(e, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}; kwargs...)::Union{Nothing, Int64}
```

Try to encode `src` into `dst` using encoder `e`.

Return the size of the encoded output in `dst` if successful.

If `dst` is too small, return `nothing`.

Throw an error if `length(src)` is not in `decoded_size_range(e)`

Otherwise throw an error.

Precondition: `dst` and `src` do not overlap in memory.

All of `dst` can be written to or used as scratch space by the encoder. Only the initial returned number of bytes are valid output.

See also [`encode_bound`](@ref) and [`decoded_size_range`](@ref)
