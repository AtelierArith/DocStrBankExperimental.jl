```
simulate!(s::DiscretizedSPAC; kwargs...)
```

SPACモデルをシミュレートし、解をs.ODESolutionに格納します。

`kwargs...`はsolve(SciML::ODEProblem; ...)に渡され、`https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/#solver_options`で文書化されています。
