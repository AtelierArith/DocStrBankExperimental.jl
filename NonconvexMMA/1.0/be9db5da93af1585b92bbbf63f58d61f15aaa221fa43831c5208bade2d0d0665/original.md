```
MMAOptions
```

A struct that stores all the options of the MMA algorithms. Th following are the fields of `MMAOptions`:

  * `maxiter`: the maximum number of inner iterations. For `MMA87`, there is 1 inner iteration per outer iteration.
  * `outer_maxiter`: the maximum number of outer iterations.
  * `maxinner`: the maximum number of inner iterations per outer iteration of [`MMA02`](@ref). Not applicable for [`MMA87`](@ref).
  * `tol`: a tolerance struct of type [`Tolerance`](@ref).
  * `s_init`: defined in the original [`MMA02`](@ref) paper.
  * `s_incr`: defined in the original [`MMA02`](@ref) paper.
  * `s_decr`: defined in the original [`MMA02`](@ref) paper.
  * `store_trace`: if true, a trace will be stored.
  * `dual_options`: the options passed to the dual optimizer from [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl).
  * `convcriteria`: an instance of [`ConvergenceCriteria`](@ref) that specifies the convergence criteria of the MMA algorithm.
  * `verbose`: true/false, when true prints convergence statistics.
