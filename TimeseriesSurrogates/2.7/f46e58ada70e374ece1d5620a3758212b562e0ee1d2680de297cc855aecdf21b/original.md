```
PartialRandomization(α = 0.5)
```

`PartialRandomization` surrogates[^Ortega1998] are similar to [`RandomFourier`](@ref) phase surrogates, but during the phase randomization step, instead of drawing phases from `[0, 2π]`, phases are drawn from `[0, 2π]*α`, where `α ∈ [0, 1]`. The authors refers to `α` as the "degree" of phase randomization, where `α = 0` means `0 %` randomization and `α = 1` means `100 %` randomization.

See [`RelativePartialRandomization`](@ref) and [`SpectralPartialRandomization`](@ref) for alternative partial-randomization algorithms

[^Ortega1998]: Ortega, Guillermo J.; Louis, Enrique (1998). Smoothness Implies Determinism in Time Series: A Measure Based Approach. Physical Review Letters, 81(20), 4345–4348. doi:10.1103/PhysRevLett.81.4345
