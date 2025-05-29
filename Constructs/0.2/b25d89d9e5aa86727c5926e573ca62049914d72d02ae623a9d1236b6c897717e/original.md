```
PaddedString([T], n, [encoding]) -> Construct{T}
```

String padded to `n` bytes.

# Arguments

  * `T<:AbstractString`: the underlying string type.
  * `n::Integer`: the size of the string in bytes.
  * `encoding::Union{Encoding, String}`: the string encoding.
