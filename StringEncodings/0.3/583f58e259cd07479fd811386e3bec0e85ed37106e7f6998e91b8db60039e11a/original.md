```
decode([T,] a::AbstractVector{UInt8}, enc)
```

Convert an array of bytes `a` representing text in encoding `enc` to a string of type `T`. By default, a `String` is returned.

To `decode` an `s::String` of data in non-UTF-8 encoding, use `decode(codeunits(s), enc)` to act on the underlying byte array.

`enc` can be specified either as a string or as an `Encoding` object. The input data `a` can be a `Vector{UInt8}` of bytes, a contiguous subarray thereof, or the `codeunits` of a `String` (or substring thereof).
