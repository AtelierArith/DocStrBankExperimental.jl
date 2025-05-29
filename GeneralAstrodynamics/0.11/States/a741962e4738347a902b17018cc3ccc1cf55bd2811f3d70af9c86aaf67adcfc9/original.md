```julia
struct CR3BPParameters{F, MU, LU, TU, AU, B} <: GeneralAstrodynamics.States.ParameterVector{F, MU, LU, TU, AU, 1, (:μ,), B}
```

All parameters required for the Circular Restricted Three-body Problem.
