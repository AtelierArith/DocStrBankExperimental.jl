```
Probe{S,T,U<:Union{Quaternion{T},Nothing},V<:Union{Matrix,Nothing},W<:Union{Nothing,Bool}}
```

Parametric type used for tracking. The orbital/spin part can contain  either scalars or `TPS`s. If spin is included, the field `Q` is a `Quaternion`  with the same type as `x`, else `Q` is `nothing`. If radiation is included,  the field `E` contains the FD matrix with `eltype(E)==S`, else `E` is `nothing`.

If all planes are exhibiting pseudo-harmonic oscillations, then `idpt` is `nothing`.  If the last plane is coasting, then `idpt` specifies which variable in the last plane  is constant (energy-like): `idpt=false` if the variable with index `NV-1` is constant, or  `idpt=true` is the variable with index `NV` is constant.
