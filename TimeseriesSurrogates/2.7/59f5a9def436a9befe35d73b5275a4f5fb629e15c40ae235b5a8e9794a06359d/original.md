```
PartialRandomizationAAFT(α = 0.5)
```

`PartialRandomizationAAFF` surrogates are similar to [`PartialRandomization`](@ref) surrogates[^Ortega1998], but adds a rescaling step, so that the surrogate has the same values as the original time series (analogous to the rescaling done for [`AAFT`](@ref) surrogates). Partial randomization surrogates have, to the package authors' knowledge, not been published in scientific literature.

[^Ortega1998]: Ortega, Guillermo J.; Louis, Enrique (1998). Smoothness Implies Determinism in Time Series: A Measure Based Approach. Physical Review Letters, 81(20), 4345–4348. doi:10.1103/PhysRevLett.81.4345
