```julia
iter = CommonSolve.init(args...; kwargs...)
```

Solves an equation or other mathematical problem using the algorithm specified in the arguments. Generally, the interface is:

```julia
iter = CommonSolve.init(prob::ProblemType,alg::SolverType; kwargs...)::IterType
CommonSolve.solve!(iter)::SolutionType
```

where the keyword arguments are uniform across all choices of algorithms. The `iter` type will be different for the different problem types.
