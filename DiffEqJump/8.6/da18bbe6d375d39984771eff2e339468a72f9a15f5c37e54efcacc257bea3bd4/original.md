```julia
struct VariableRateJump{R, F, I, T, T2} <: DiffEqJump.AbstractJump
```

Defines a jump process with a rate (i.e. hazard, intensity, or propensity) that may explicitly depend on time. More precisely, one where the rate function is allowed to change *between* the occurrence of jumps. For detailed examples and usage information see the

  * [Tutorial](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/)

## Fields

  * `rate`: Function `rate(u,p,t)` that returns the jump's current rate.
  * `affect!`: Function `affect(integrator)` that updates the state for one occurrence of the jump.
  * `idxs`
  * `rootfind`
  * `interp_points`
  * `save_positions`
  * `abstol`
  * `reltol`

## Examples

Suppose `u[1]` gives the amount of particles and `t*p[1]` the probability per time each particle can decay away. A corresponding `VariableRateJump` for this jump process is

```julia
rate(u,p,t) = t*p[1]*u[1]
affect!(integrator) = integrator.u[1] -= 1
crj = VariableRateJump(rate, affect!)
```

## Notes

  * **`VariableRateJump`s result in `integrator`s storing an effective state type that wraps the main state vector.** See [`ExtendedJumpArray`](@ref) for details on using this object. Note that the presence of *any* `VariableRateJump`s will result in all `ConstantRateJump`, `VariableRateJump` and callback `affect!` functions receiving an integrator with `integrator.u` an [`ExtendedJumpArray`](@ref).
  * Must be used with `ODEProblem`s or `SDEProblem`s to be correctly simulated (i.e. can not currently be used with `DiscreteProblem`s).
  * Salis H., Kaznessis Y.,  Accurate hybrid stochastic simulation of a system of coupled chemical or biochemical reactions, Journal of Chemical Physics, 122 (5), DOI:10.1063/1.1835951 is used for calculating jump times with `VariableRateJump`s within ODE/SDE integrators.
