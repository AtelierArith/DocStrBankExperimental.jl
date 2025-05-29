```
local_growth_rates(ds::DynamicalSystem, points::StateSpaceSet; kwargs...) → λlocal
```

Compute the local exponential growth rate(s) of perturbations of the dynamical system `ds` for initial conditions given in `points`. For each initial condition `u ∈ points`, `S` total perturbations are created and evolved exactly for time `Δt`. The exponential local growth rate is defined simply by `log(g/g0)/Δt` with `g0` the initial perturbation size and `g` the size after `Δt`. Thus, `λlocal` is a matrix of size `(length(points), S)`.

This function is a modification of [`lyapunov`](@ref). It uses the full nonlinear dynamics and a [`ParallelDynamicalSystem`](@ref) to evolve the perturbations, but does not do any re-scaling, thus allowing probing state and time dependence of perturbation growth. The actual growth is given by `exp(λlocal * Δt)`.

The output of this function is sometimes called "Nonlinear Local Lyapunov Exponent".

## Keyword arguments

  * `S = 100`
  * `Δt = 5`
  * `perturbation`: If given, it should be a function `perturbation(ds, u, j)` that outputs a perturbation vector (preferrably `SVector`) given the system, current initial condition `u` and the counter `j ∈ 1:S`. If not given, a random perturbation is generated with norm given by the keyword `e = 1e-6`.
