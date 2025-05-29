```
NullTerminatedString([T], [encoding]) -> Construct{T}
```

String ending in a terminating null character.

This is the default construct for the subtypes of `AbstractString`.

# Arguments

  * `T<:AbstractString`: the underlying string type.
  * `encoding::Union{Encoding, String}`: the string encoding.
