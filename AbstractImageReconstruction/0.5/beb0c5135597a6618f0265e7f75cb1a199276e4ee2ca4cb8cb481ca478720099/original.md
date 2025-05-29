```
clear!(plan::RecoPlan{T}, preserve::Bool = true) where {T<:AbstractImageReconstructionParameters}
```

Clear all properties of `plan`. If `preserve` is `true`, nested `RecoPlan`s are preserved.
