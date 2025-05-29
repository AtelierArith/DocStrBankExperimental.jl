```
encode_bound(e, src_size::Int64)::Int64
```

Return the size of `dst` required to ensure [`try_encode!`](@ref) succeeds regardless of `src`'s content if `src_size` is also in [`decoded_size_range(e)`](@ref) and there is enough memory.

On the domain of `0:typemax(Int64)` this function must not error and must be monotonically increasing.
