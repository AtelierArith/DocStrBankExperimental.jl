```
setAll!(plan::RecoPlan{T}, name::Symbol, x) where {T<:AbstractImageReconstructionParameters}
```

Recursively set the property `name` of each nested `RecoPlan` of `plan` to `x`.
