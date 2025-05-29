```
coulombs!(F, F′, G, G′, x::AbstractVector, η, ℓ; kwargs...)
```

Loop through all values of `x` and compute all Coulomb functions, storing the results in the preallocated matrices `F`, `F′`, `G`, `G′`.
