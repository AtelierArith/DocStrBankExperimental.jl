```
try_find_decoded_size(d, src::AbstractVector{UInt8})::Union{Nothing, Int64}
```

Try to return the size of the decoded output of `src` using `d`.

If the size cannot be quickly determined, return `nothing`.

If the encoded data is found to be invalid, throw a `DecodingError`.

This if an `Int64` is returned, it must be the exact size of the decoded output. If [`try_decode!`](@ref) is called with a `dst` of this size, it must succeed and return the same size, or throw an error.
