```
decode!(d, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}) -> dst
```

Decode the input data `src` into `dst` using decoder `d`. `d` must implement [`try_decode!`](@ref).

Throw a [`DecodedSizeError`](@ref) if the decoded output size is not exactly `length(dst)`.

Throw a [`DecodingError`](@ref) if decoding fails because the input data is not valid.

Otherwise throw an error.

Precondition: `dst` and `src` do not overlap in memory.

See also [`decode`](@ref) and [`encode`](@ref)
