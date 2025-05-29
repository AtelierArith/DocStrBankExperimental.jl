```
PrefixedArray([TA], S|size, T|element) -> Construct{TA}
```

Defines an array with its size in the header.

# Arguments

  * `TA<:AbstractArray{T, N}`: the target array type, the default is `Array{T, N}`.
  * `S<:Union{Integer, NTuple{N, Integer}}`: the type of the size in the header.
  * `T`: the type of elements.
  * `size::Construct{S}`: the construct of size.
  * `element::Construct{T}`: the construct of elements.
