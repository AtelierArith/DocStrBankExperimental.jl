```
decode(d, src::AbstractVector{UInt8}; max_size::Integer=typemax(Int64), size_hint::Integer=Int64(0))::Vector{UInt8}
```

Decode the input data `src` using decoder `d`. `d` must implement [`try_find_decoded_size`](@ref), [`try_decode!`](@ref), and optionally [`try_resize_decode!`](@ref).

Throw a [`DecodedSizeError`](@ref) if decoding fails because the output size would be greater than `max_size`.

Throw a [`DecodingError`](@ref) if decoding fails because the input data is not valid.

Otherwise throw an error.

If you have a good idea of what the decoded size is, using the `size_hint` keyword argument can greatly improve performance.

See also [`DecodeOptions`](@ref) and [`encode`](@ref)
