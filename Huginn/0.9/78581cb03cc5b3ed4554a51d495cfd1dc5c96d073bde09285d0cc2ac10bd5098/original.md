Constructs a `SolverParameters` object with the specified parameters or using default values.

```
SolverParameters(; solver::OrdinaryDiffEq.OrdinaryDiffEqAdaptiveAlgorithm = RDPK3Sp35(),
                  reltol::F = 1e-12,
                  step::F = 1.0/12.0,
                  tstops::Union{Nothing,Vector{F}} = nothing,
                  save_everystep = false,
                  progress::Bool = true,
                  progress_steps::I = 10) where {F <: AbstractFloat, I <: Integer}
```

# Arguments

  * `solver::OrdinaryDiffEq.OrdinaryDiffEqAdaptiveAlgorithm`: The ODE solver algorithm to use. Defaults to `RDPK3Sp35()`.
  * `reltol::F`: The relative tolerance for the solver. Defaults to `1e-12`.
  * `step::F`: The step size for the callbacks. These are mainly used to run the surface mass balance model. Defaults to `1.0/12.0` (i.e. a month).
  * `tstops::Union{Nothing, Vector{F}}`: Optional vector of time points where the solver should stop. Defaults to `nothing`.
  * `save_everystep::Bool`: Whether to save the solution at every step. Defaults to `false`.
  * `progress::Bool`: Whether to show progress during the solving process. Defaults to `true`.
  * `progress_steps::I`: The number of steps between progress updates. Defaults to `10`.

# Returns

  * `solver_parameters`: A `SolverParameters` object constructed with the specified parameters.
