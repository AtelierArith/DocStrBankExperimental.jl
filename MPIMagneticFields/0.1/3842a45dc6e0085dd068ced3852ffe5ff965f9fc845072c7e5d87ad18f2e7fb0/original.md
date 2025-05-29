```julia
struct NegativeField{T<:MPIMagneticFields.AbstractMagneticField} <: MPIMagneticFields.AbstractNegativeField
```

Container for negative fields.

The field of this container is interpreted as being the negative of `field`.
