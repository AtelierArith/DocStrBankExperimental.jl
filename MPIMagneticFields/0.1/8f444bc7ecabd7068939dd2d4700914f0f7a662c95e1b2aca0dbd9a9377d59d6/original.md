```julia
struct SequencedField{FT<:MPIMagneticFields.AbstractMagneticField, ST<:MPIMagneticFields.Sequence} <: MPIMagneticFields.AbstractSequencedField
```

Container for sequenced fields.

Attaches a sequence to a field defining the movement over time.
