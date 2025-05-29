```
intensity(f, t)
```

Compute the intensity *envelope* of the field `f` at time `t` by applying [`phase_shift`](@ref) to the [`carrier`](@ref) and looking for the maximal [`instantaneous_intensity`](@ref).
