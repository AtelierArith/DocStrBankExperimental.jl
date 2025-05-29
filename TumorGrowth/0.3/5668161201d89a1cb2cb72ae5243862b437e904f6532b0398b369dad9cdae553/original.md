```
logistic(times, v0, v∞, ω)
```

Return volumes for specified `times`, based on anaytic solutions to the classical logistic (Verhulst) model for lesion growth. Here `p` will have properties `v0`, `v∞`, `ω`, where `v0` is the volume at time `times[1]`.

This is the `λ=-1` case of the [`bertalanffy`](@ref) model.

For a list of all models see [`TumorGrowth`](@ref). 
