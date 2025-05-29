```
try_decode!(d, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}; kwargs...)::Union{Nothing, Int64}
```

Try to decode `src` into `dst` using decoder `d`.

Return the size of the decoded output in `dst` if successful.

If `dst` is too small to fit the decoded output, return `nothing`.

Throw a [`DecodingError`](@ref) if decoding fails because the input data is not valid.

Otherwise throw an error.

Precondition: `dst` and `src` do not overlap in memory.

All of `dst` can be written to or used as scratch space by the decoder. Only the initial returned number of bytes are valid output.
