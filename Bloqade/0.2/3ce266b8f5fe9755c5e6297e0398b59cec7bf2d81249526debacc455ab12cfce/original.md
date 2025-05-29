```
get_average_rydberg_densities(atoms, reg; [C=2π * 862690 * MHz*µm^6], Ω[, ϕ, Δ], [dt=1e-3 * μs])
```

Return average Rydberg densities throughout an evolution.

# Arguments

  * `atoms`: a collection of atom positions.
  * `reg`: required, the register object.

# Keyword Arguments

  * `C`: optional, default unit is `MHz*µm^6`, interation parameter,   see also [`RydInteract`](@ref).
  * `Ω`: optional, default unit is `MHz`, Rabi frequencies, divided by 2, see also [`SumOfX`](@ref).
  * `ϕ`: optional, does not have unit, the phase, see [`SumOfXPhase`](@ref).
  * `Δ`: optional, default unit is `MHz`, detuning parameter, see [`SumOfN`](@ref).
  * `dt`: optional, default unit is `μs`, time step for the evolution.
  * `solver`: optional, default solver is `Vern8()`, the solver for the SchrodingerProblem, see [`SchrodingerProblem`](@ref).
