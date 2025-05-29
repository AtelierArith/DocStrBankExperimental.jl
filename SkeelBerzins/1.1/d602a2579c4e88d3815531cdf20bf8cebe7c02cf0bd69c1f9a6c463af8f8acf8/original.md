```
ODEProblem(problem)
```

Generate an [ODEProblem](https://docs.sciml.ai/DiffEqDocs/stable/types/ode_types/#SciMLBase.ODEProblem) from the [`ODEFunction`](@ref) which then can be solved by using the [solve](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) method.

Input arguments:

  * `problem`: Structure of type [`SkeelBerzins.ProblemDefinition`](@ref).
