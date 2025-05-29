```
init_mutunerlogger(;
    # KEYWORD ARGUMENTS
    target_density::T,
    inverse_temperature::T,
    system_size::Int,
    intensive_energy_scale::T = 1.0,
    initial_chemical_potential::T = 0.0,
    memory_fraction::T = 0.5,
    complex_sign_problem::Bool = false,
) where {T<:AbstractFloat}
```

Initializes a [`MuTunerLogger`](@ref) instance with the given parameters.

# Keyword Arguments

  * `target_density::T`: Target particle density $\langle n \rangle$.
  * `inverse_temperature::T`: Inverse temperature $\beta$.
  * `system_size::Int`: System size $V$.
  * `intensive_energy_scale::T = 1.0`: Characteristic intensive energy scale $u_0$.
  * `initial_chemical_potential::T = 0.0`: Initial guess for chemical potential $\mu$.
  * `memory_fraction::T = 0.5`: Fraction of measurement history that is retained and used when calculating forgetful averages and variances.
  * `complex_sign_problem::Bool = false`: If true, then the Monte Carlo simulation suffers from a complex sign problem wherein the Monte Carlo weights are complex.
