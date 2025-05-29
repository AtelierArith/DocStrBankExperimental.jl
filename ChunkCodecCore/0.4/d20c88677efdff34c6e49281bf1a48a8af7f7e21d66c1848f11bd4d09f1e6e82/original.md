```
try_resize_decode!(d, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}, max_size::Int64; kwargs...)::Union{Nothing, Int64}
```

Try to decode the input `src` into `dst` using decoder `d`.

Return the size of the decoded output in `dst` if successful.

If `dst` is too small, resize `dst` and try again. If the `max_size` limit will be passed, return `nothing`.

`dst` can be resized using the `resize!` function to any size between the original length of `dst` and `max_size`.

Throw an `ArgumentError` if `length(dst)` is not in `0:max_size`.

Precondition: `dst` and `src` do not overlap in memory.

All of `dst` can be written to or used as scratch space by the decoder. Only the initial returned number of bytes are valid output.

If the size of `dst` is increased, its length will be equal to the returned number of bytes.
