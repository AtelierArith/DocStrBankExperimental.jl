```julia
mutable struct KeplerianState{F, LU, TU, AU} <: GeneralAstrodynamics.States.StateVector{F, LU, TU, AU, (e = 1, a = 2, i = 3, Ω = 4, ω = 5, ν = 6)}
```

A Keplerian state vector with length 6. Internally uses `MVector` and `LVector` to store data. Data is accessible via labels, which are `e, a, i, Ω, ω, ν`.
