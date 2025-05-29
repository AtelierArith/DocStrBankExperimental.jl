```
try_resize_decode!(d, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}, max_size::Int64; kwargs...)::Union{Nothing, Int64}
```

Try to decode the input `src` into `dst` using decoder `d`.

Return the size of the decoded output in `dst` if successful.

`dst` can be grown using the `resize!` function to any size between one more than the original length of `dst` and `max_size`.

Return `nothing` if the size of `dst` is too small to contain the decoded output and cannot be grown due to the `max_size` restriction.

Precondition: `dst` and `src` do not overlap in memory.

All of `dst` can be written to or used as scratch space by the decoder. Only the initial returned number of bytes are valid output.
