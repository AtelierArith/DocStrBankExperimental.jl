```
apply_section!(Y::AT, λY::GlobalSection{T, AT}, Y₂::AT) where {T, AT<:StiefelManifold{T}}
```

Apply `λY` to `Y₂` and store the result in `Y`.

This is the inplace version of [`apply_section`](@ref).
