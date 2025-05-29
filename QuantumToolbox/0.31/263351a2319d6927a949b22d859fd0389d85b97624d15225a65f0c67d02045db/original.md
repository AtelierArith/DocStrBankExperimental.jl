```
multisite_operator(dims::Union{AbstractVector, Tuple}, pairs::Pair{<:Integer,<:QuantumObject}...)
```

A Julia function for generating a multi-site operator $\\hat{O} = \\hat{O}_i \\hat{O}_j \\cdots \\hat{O}_k$. The function takes a vector of dimensions `dims` and a list of pairs `pairs` where the first element of the pair is the site index and the second element is the operator acting on that site.

# Arguments

  * `dims::Union{AbstractVector, Tuple}`: A vector of dimensions of the lattice.
  * `pairs::Pair{<:Integer,<:QuantumObject}...`: A list of pairs where the first element of the pair is the site index and the second element is the operator acting on that site.

# Returns

`QuantumObject`: A `QuantumObject` representing the multi-site operator.

# Example

```jldoctest
julia> op = multisite_operator(Val(8), 5=>sigmax(), 7=>sigmaz());

julia> op.dims
8-element StaticArraysCore.SVector{8, Int64} with indices SOneTo(8):
 2
 2
 2
 2
 2
 2
 2
 2
```
