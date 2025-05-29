```
madnlp(model::AbstractNLPModel; options...)
```

Build a [`MadNLPSolver`](@ref) and solve it using the interior-point method. Return the solution as a [`MadNLPExecutionStats`](@ref).
