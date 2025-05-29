```
liouvillian_generalized(H::QuantumObject, fields::Vector, 
T_list::Vector; N_trunc::Int=size(H,1), tol::Float64=0.0, σ_filter::Union{Nothing, Real}=nothing)
```

Constructs the generalized Liouvillian for a system coupled to a bath of harmonic oscillators.

See, e.g., Settineri, Alessio, et al. "Dissipation and thermal noise in hybrid quantum systems in the ultrastrong-coupling regime." Physical Review A 98.5 (2018): 053834.
