```
apply_section(λY::GlobalSection{T, AT}, Y₂::AT) where {T, AT <: StiefelManifold{T}}
```

Apply `λY` to `Y₂`.

Mathematically this is the group action of the element $\lambda{}Y\in{}G$ on the element $Y_2$ of the homogeneous space $\mathcal{M}$.

Internally it calls [`apply_section!`](@ref).
