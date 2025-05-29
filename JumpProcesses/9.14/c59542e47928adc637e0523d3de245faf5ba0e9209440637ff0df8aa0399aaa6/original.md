```julia
struct ConstantRateJump{F1, F2} <: JumpProcesses.AbstractJump
```

Defines a jump process with a rate (i.e. hazard, intensity, or propensity) that does not *explicitly* depend on time. More precisely, one where the rate function is constant *between* the occurrence of jumps. For detailed examples and usage information, see the

  * [Tutorial](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)

## Fields

  * `rate`: Function `rate(u,p,t)` that returns the jump's current rate.
  * `affect!`: Function `affect(integrator)` that updates the state for one occurrence of the jump.

## Examples

Suppose `u[1]` gives the number of particles and `p[1]` the probability per time each particle can decay away. A corresponding `ConstantRateJump` for this jump process is

```julia
rate(u,p,t) = p[1]*u[1]
affect!(integrator) = integrator.u[1] -= 1
crj = ConstantRateJump(rate, affect!)
```

Notice, here that `rate` changes in time, but is constant between the occurrence of jumps (when `u[1]` will decrease).
