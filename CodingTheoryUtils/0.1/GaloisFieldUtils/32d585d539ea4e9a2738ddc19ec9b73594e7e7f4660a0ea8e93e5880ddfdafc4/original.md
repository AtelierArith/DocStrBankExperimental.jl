```
primitive_root(FF::Type{<:GaloisFields.AbstractGaloisField})::GaloisFields.AbstractGaloisField
```

Find a primitive root of the finite field.

# Arguments

  * `FF::Type{<:GaloisFields.AbstractGaloisField}`: A finite field type

# Returns

  * A primitive root of the finite field

# Notes

  * A primitive root is an element that generates the multiplicative group of the field
  * The multiplicative group of a finite field is cyclic

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
primitive_root(F4) == α

GF2 = GaloisField(2)
primitive_root(GF2) == GF2(1)
```
