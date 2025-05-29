```julia
struct JumpSet{T1, T2, T3, T4} <: JumpProcesses.AbstractJump
```

Defines a collection of jumps that should collectively be included in a simulation.

## Fields

  * `variable_jumps`: Collection of [`VariableRateJump`](@ref)s
  * `constant_jumps`: Collection of [`ConstantRateJump`](@ref)s
  * `regular_jump`: Collection of [`RegularJump`](@ref)s
  * `massaction_jump`: Collection of [`MassActionJump`](@ref)s

## Examples

Here we construct two jumps, store them in a `JumpSet`, and then simulate the resulting process.

```julia
using JumpProcesses, OrdinaryDiffEq

rate1(u,p,t) = p[1]
affect1!(integrator) = (integrator.u[1] += 1)
crj = ConstantRateJump(rate1, affect1!)

rate2(u,p,t) = (t/(1+t))*p[2]*u[1]
affect2!(integrator) = (integrator.u[1] -= 1)
vrj = VariableRateJump(rate2, affect2!)

jset = JumpSet(crj, vrj)

f!(du,u,p,t) = (du .= 0)
u0 = [0.0]
p = (20.0, 2.0)
tspan = (0.0, 200.0)
oprob = ODEProblem(f!, u0, tspan, p)
jprob = JumpProblem(oprob, Direct(), jset)
sol = solve(jprob, Tsit5())
```
