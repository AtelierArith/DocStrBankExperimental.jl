```julia
struct SuperimposedField{T<:MPIMagneticFields.AbstractMagneticField, U<:MPIMagneticFields.AbstractMagneticField} <: MPIMagneticFields.AbstractSuperimposedField
```

Container for superimposed fields.

The fields in `fieldA` and `fieldB` are interpreted as being linearily superimposed.
