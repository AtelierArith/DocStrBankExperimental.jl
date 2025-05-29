```
ODEProblem(problem)
```

[`ODEFunction`](@ref)から生成された[ODEProblem](https://docs.sciml.ai/DiffEqDocs/stable/types/ode_types/#SciMLBase.ODEProblem)は、[solve](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)メソッドを使用して解決できます。

入力引数:

  * `problem`: [`SkeelBerzins.ProblemDefinition`](@ref)型の構造体。
