```julia
struct LimitedSequencedField{SFT<:MPIMagneticFields.AbstractSequencedField, T<:Number} <: MPIMagneticFields.AbstractSequencedField
```

Container for limited sequenced fields.

Applies field limits to a sequenced field.
