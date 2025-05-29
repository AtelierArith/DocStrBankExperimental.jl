```
F2p(b::Vector{Fb}, α::Fe)::Fe
```

Convert a vector of F2 elements to a field element using the given basis element.

# Arguments

  * `b::Vector{Fb}`: A vector of F2 elements
  * `α::Fe`: A basis element of the target field

# Returns

  * `Fe`: The field element represented by the vector

# Throws

  * `AssertionError`: If the length of the input vector does not match the extension degree of the field

# Examples

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> F2p([F2(1), F2(0)], α)
1
```
