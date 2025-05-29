```
field_size(FF::Type{<:GaloisFields.AbstractGaloisField})::Int
```

Calculate the size of the finite field.

# Arguments

  * `FF::Type{<:GaloisFields.AbstractGaloisField}`: A finite field type

# Returns

  * The size of the finite field

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
field_size(F4) == 4
```
