```
steadystate(M::AbstractHEOMLSMatrix; solver, verbose, SOLVEROptions...)
```

Solve the steady state of the auxiliary density operators based on `LinearSolve.jl` (i.e., solving $x$ where $A \times x = b$).

# Parameters

  * `M::AbstractHEOMLSMatrix` : the matrix given from HEOM model, where the parity should be `EVEN`.
  * `solver::SciMLLinearSolveAlgorithm` : solver in package `LinearSolve.jl`. Default to `KrylovJL_BICGSTAB(rtol=1e-12, atol=1e-14)`.
  * `verbose::Bool` : To display verbose output and progress bar during the process or not. Defaults to `true`.
  * `SOLVEROptions` : extra options for solver

# Notes

  * For more details about `solver` and `SOLVEROptions`, please refer to [`LinearSolve.jl`](http://linearsolve.sciml.ai/stable/)

# Returns

  * `::ADOs` : The steady state of auxiliary density operators.
