```
F2p(Fe::Type{<:GaloisFields.AbstractExtensionField}, b::Vector{Fb})::Fe
```

Convert a vector of F2 elements to a field element using the primitive element of the field.

# Arguments

  * `Fe::Type{<:GaloisFields.AbstractExtensionField}`: The target field type
  * `b::Vector{Fb}`: A vector of F2 elements

# Returns

  * `Fe`: The field element represented by the vector

# Throws

  * `AssertionError`: If the length of the input vector does not match the extension degree of the field

# Examples

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> F2p(F4, [F2(1), F2(0)])
1
```
