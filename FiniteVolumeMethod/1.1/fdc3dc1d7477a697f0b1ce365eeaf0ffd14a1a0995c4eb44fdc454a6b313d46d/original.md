```
solve(prob::AbstractFVMTemplate, args...; kwargs...)
```

Solve the problem `prob` using the standard `solve` interface from DifferentialEquations.jl. For  steady state problems, the interface is from LinearSolve.jl.
