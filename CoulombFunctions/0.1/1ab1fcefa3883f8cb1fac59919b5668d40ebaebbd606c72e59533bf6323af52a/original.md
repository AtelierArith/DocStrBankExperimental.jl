```
coulombs!(F, F′, G, G′, r, Z, k::AbstractVector, ℓ; kwargs...)
```

Loop through all values of `k` and compute all Coulomb functions, storing the results in the preallocated matrices `F`, `F′`, `G`, `G′`. `x=k*r` and `η≡-Z/k`, i.e. `Z>0` for attractive potentials.
