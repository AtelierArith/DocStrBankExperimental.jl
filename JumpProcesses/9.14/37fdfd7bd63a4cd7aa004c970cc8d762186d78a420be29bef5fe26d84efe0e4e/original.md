```julia
struct SSAStepper <: SciMLBase.AbstractDEAlgorithm
```

Highly efficient integrator for pure jump problems that involve only `ConstantRateJump`s, `MassActionJump`s, and/or `VariableRateJump`s *with rate bounds*.

## Notes

  * Only works with `JumpProblem`s defined from `DiscreteProblem`s.
  * Only works with collections of `ConstantRateJump`s, `MassActionJump`s, and `VariableRateJump`s with rate bounds.
  * Only supports `DiscreteCallback`s for events, which are checked after every step taken by `SSAStepper`.
  * Only supports a limited subset of the output controls from the common solver interface, specifically `save_start`, `save_end`, and `saveat`.
  * As when using jumps with ODEs and SDEs, saving controls for whether to save each time a jump occurs are via the `save_positions` keyword argument to `JumpProblem`. Note that when choosing `SSAStepper` as the timestepper, `save_positions = (true,true)`, `(true,false)`, or `(false,true)` are all equivalent. `SSAStepper` will save only the post-jump state in the solution object in each of these cases. This is because solution objects generated via `SSAStepper` use piecewise-constant interpolation, and can therefore exactly reconstruct the sampled jump process path with knowing just the post-jump state. That is, `sol(t)` for any `0 <= t <= tstop` will give the exact value of the sampled solution path at `t` provided at least one component of `save_positions` is `true`.

## Examples

SIR model:

```julia
using JumpProcesses
β = 0.1 / 1000.0; ν = .01;
p = (β,ν)
rate1(u,p,t) = p[1]*u[1]*u[2]  # β*S*I
function affect1!(integrator)
  integrator.u[1] -= 1         # S -> S - 1
  integrator.u[2] += 1         # I -> I + 1
end
jump = ConstantRateJump(rate1,affect1!)

rate2(u,p,t) = p[2]*u[2]      # ν*I
function affect2!(integrator)
  integrator.u[2] -= 1        # I -> I - 1
  integrator.u[3] += 1        # R -> R + 1
end
jump2 = ConstantRateJump(rate2,affect2!)
u₀    = [999,1,0]
tspan = (0.0,250.0)
prob = DiscreteProblem(u₀, tspan, p)
jump_prob = JumpProblem(prob, Direct(), jump, jump2)
sol = solve(jump_prob, SSAStepper())
```

see the [tutorial](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/) for details.
