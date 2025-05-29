```julia
DiffEqBase.DiscreteProblemExpr(sys::JumpSystem, u0map, tspan,
                               parammap = DiffEqBase.NullParameters; kwargs...)
```

Generates a blank DiscreteProblem for a JumpSystem to utilize as its solving `prob.prob`. This is used in the case where there are no ODEs and no SDEs associated with the system.

Continuing the example from the [`JumpSystem`](@ref) definition:

```julia
using DiffEqBase, JumpProcesses
u₀map = [S => 999, I => 1, R => 0]
parammap = [β => 0.1 / 1000, γ => 0.01]
tspan = (0.0, 250.0)
dprob = DiscreteProblem(js, u₀map, tspan, parammap)
```
