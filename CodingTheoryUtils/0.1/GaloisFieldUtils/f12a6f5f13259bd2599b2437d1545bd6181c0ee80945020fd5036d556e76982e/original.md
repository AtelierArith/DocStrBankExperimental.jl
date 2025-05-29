```
field_size(a::GaloisFields.AbstractGaloisField)::Int
```

Calculate the size of the finite field.

# Arguments

  * `a::GaloisFields.AbstractGaloisField`: A finite field element

# Returns

  * The size of the finite field

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
field_size(α) == 4
```
