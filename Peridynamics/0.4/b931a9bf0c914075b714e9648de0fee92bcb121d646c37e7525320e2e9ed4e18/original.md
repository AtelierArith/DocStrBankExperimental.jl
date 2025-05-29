```
DynamicRelaxation(; kwargs...)
```

Time integration solver for the adaptive dynamic relaxation algorithm used for quasi-static simulations.

# Keywords

  * `steps::Int`: Number of calculated time steps. If this keyword is specified, the keyword   `time` is no longer allowed.
  * `stepsize::Real`: Manually specify the size of the time step. (default: `1.0`)
  * `damping_factor::Real`: Damping factor to increase the value in the mass matrix.   (default: `1.0`)

# Throws

  * Error if `steps < 0`.
  * Error if `stepsize < 0`.
  * Error if `damping_factor < 0`.

# Example

```julia-repl
julia> DynamicRelaxation(steps=1000)
DynamicRelaxation:
  n_steps  1000
  Δt       1
  Λ        1

julia> DynamicRelaxation(steps=1000, damping_factor=2)
DynamicRelaxation:
  n_steps  1000
  Δt       1
  Λ        2
```
