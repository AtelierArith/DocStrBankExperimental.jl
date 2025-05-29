```
is_primitive(a::GaloisFields.AbstractGaloisField)::Bool
```

Check if an element is a primitive root of the finite field.

# Arguments

  * `a::GaloisFields.AbstractGaloisField`: A finite field element

# Returns

  * `true` if the element is a primitive root, `false` otherwise

# Notes

  * A primitive root is an element that generates the multiplicative group of the field
  * The multiplicative group of a finite field is cyclic

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
is_primitive(α) == true
is_primitive(F4(1)) == false

GF2 = GaloisField(2)
is_primitive(GF2(1)) == true # Special case for GF(2)
```
