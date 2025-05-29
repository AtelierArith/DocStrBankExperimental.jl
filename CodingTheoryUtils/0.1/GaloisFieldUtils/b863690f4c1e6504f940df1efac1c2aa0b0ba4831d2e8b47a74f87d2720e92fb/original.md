```
extension_degree(ff::Type{<:GaloisFields.AbstractGaloisField})::Int
```

Calculate the extension degree of the finite field.

# Arguments

  * `ff::Type{<:GaloisFields.AbstractGaloisField}`: A finite field type

# Returns

  * The extension degree of the finite field

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
extension_degree(F4) == 2

GF2 = GaloisField(2)
extension_degree(GF2) == 1
```
