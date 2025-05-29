```julia
DiffEqBase.JumpProblem(js::JumpSystem, prob, aggregator; kwargs...)
```

Generates a JumpProblem from a JumpSystem.

Continuing the example from the [`DiscreteProblem`](@ref) definition:

```julia
jprob = JumpProblem(js, dprob, Direct())
sol = solve(jprob, SSAStepper())
```
