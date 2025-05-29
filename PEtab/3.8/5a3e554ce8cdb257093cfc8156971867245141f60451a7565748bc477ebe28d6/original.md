```
get_startguesses(prob::PEtabODEProblem, n::Integer; kwargs...)
```

Generate `n` random parameter vectors within the parameter bounds in `prob`.

If `n = 1`, a single random vector is returned. For `n > 1`, a vector of random parameter vectors is returned. In both cases, parameter vectors are returned as a `ComponentArray`. For details on how to interact with a `ComponentArray`, see the documentation and the ComponentArrays.jl [documentation](https://github.com/jonniedie/ComponentArrays.jl).

See also [`calibrate`](@ref) and [`calibrate_multistart`](@ref).

## Keyword Arguments

  * `sampling_method = LatinHypercubeSample()`: Method for sampling a diverse (spread out) set  of parameter vectors. Any algorithm from  [QuasiMonteCarlo](https://github.com/SciML/QuasiMonteCarlo.jl) is allowed, but the  default `LatinHypercubeSample` is recommended as it usually performs well.
  * `sample_prior::Bool = true`: Whether to sample random parameter values from the  prior distribution if a parameter has a prior.
  * `allow_inf::Bool = false`: Whether to return parameter vectors for which the likelihood  cannot be computed (typically happens because the `ODEProblem` cannot be solved). Often  it only makes sense to use starting points with a computable likelihood for  parameter estimation, hence it typically does not make sense to change this option.
