```julia
DiffEqBase.ODEProblem(sys::JumpSystem, u0map, tspan,
                           parammap = DiffEqBase.NullParameters;
                           kwargs...)
```

Generates a blank ODEProblem for a pure jump JumpSystem to utilize as its `prob.prob`. This is used in the case where there are no ODEs and no SDEs associated with the system but there are jumps with an explicit time dependency (i.e. `VariableRateJump`s). If no jumps have an explicit time dependence, i.e. all are `ConstantRateJump`s or `MassActionJump`s then `DiscreteProblem` should be preferred for performance reasons.

Continuing the example from the [`JumpSystem`](@ref) definition:

```julia
using DiffEqBase, JumpProcesses
u₀map = [S => 999, I => 1, R => 0]
parammap = [β => 0.1 / 1000, γ => 0.01]
tspan = (0.0, 250.0)
oprob = ODEProblem(complete(js), u₀map, tspan, parammap)
```
