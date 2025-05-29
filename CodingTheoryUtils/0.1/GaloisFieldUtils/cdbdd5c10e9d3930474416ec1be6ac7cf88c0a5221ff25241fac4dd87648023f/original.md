```
extension_degree(a::GaloisFields.AbstractGaloisField)::Int
```

Calculate the extension degree of the finite field.

# Arguments

  * `a::GaloisFields.AbstractGaloisField`: A finite field element

# Returns

  * The extension degree of the finite field

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
extension_degree(α) == 2
```
