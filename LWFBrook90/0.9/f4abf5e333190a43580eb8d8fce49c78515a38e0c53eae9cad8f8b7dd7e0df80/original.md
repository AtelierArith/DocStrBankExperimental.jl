```
simulate!(s::DiscretizedSPAC; kwargs...)
```

Simulates a SPAC model and stores the solution in s.ODESolution.

`kwargs...` are passed through to solve(SciML::ODEProblem; ...) and are documented under `https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/#solver_options`
