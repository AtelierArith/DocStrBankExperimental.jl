```
solve!(
    method::AbstractNonlinearSolverMethod{FT},
    soltype::SolutionType = CompactSolution(),
    tol::Union{Nothing, AbstractTolerance} = nothing,
    maxiters::Union{Nothing, Int} = 10_000,
)
```

Solve the non-linear system given

  * `method` the numerical method
  * `soltype` the solution type (`CompactSolution` or `VerboseSolution`)
  * `tol` the stopping tolerance
  * `maxiters` the maximum number of iterations to perform
