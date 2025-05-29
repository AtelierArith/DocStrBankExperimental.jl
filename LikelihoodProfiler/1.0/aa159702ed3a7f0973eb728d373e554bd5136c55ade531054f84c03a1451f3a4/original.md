```
profile(plprob::PLProblem, method::AbstractProfilerMethod; 
        idxs::AbstractVector{<:Int} = eachindex(get_optpars(plprob)),
        parallel_type::Symbol=:none, kwargs...)
```

Profiles the likelihood function for the given problem `plprob` using the specified profiling `method`.

### Arguments

  * `plprob::PLProblem{ParameterProfile}`: The profiling problem instance containing the parameters and likelihood function to be profiled.
  * `method::AbstractProfilerMethod`: The method to be used for profiling.
  * `idxs::AbstractVector{<:Int}`: Indices of the parameters to be profiled. Defaults to all parameters.
  * `parallel_type::Symbol`: Specifies the type of parallelism to be used. Defaults to `:none`.
  * `maxiters::Int`: Maximum number of iterations for one branch (left and right) of the profiling process. Defaults to `1e4`.
  * `verbose::Bool`: Indicates whether to display the progress of the profiling process. Defaults to `false`.

### Returns

  * Returns the profiling results `PLSolution`.

### Example

```julia
plprob = PLProblem(optprob, optpars, [(-10.,10.), (-5.,5.)])
method = OptimizationProfiler(optimizer = Optimization.LBFGS(), stepper = FixedStep())
sol = profile(plprob, method; idxs=[1])
```
