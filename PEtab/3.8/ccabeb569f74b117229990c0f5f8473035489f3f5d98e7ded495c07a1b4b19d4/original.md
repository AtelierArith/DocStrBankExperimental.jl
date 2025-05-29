```
calibrate_multistart(prob::PEtabODEProblem, alg, nmultistarts::Integer; nprocs = 1,
                     dirsave=nothing, kwargs...)::PEtabMultistartResult
```

Perform `nmultistarts` parameter estimation runs from randomly sampled starting points using the optimization algorithm `alg` to estimate the unknown model parameters in `prob`.

A list of available and recommended optimisation algorithms (`alg`) can be found in the package documentation and in the [`calibrate`](@ref) documentation.

If `nprocs > 1`, the parameter estimation runs are performed in parallel using the [`pmap`](https://docs.julialang.org/en/v1/stdlib/Distributed/#Distributed.pmap) function from Distributed.jl with `nprocs` processes. If parameter estimation on a single process (`nprocs = 1`) takes longer than 5 minutes, we **strongly** recommend setting `nprocs > 1`, as this can greatly reduce runtime. Note that `nprocs` should not be larger than the number of cores on the computer.

If `dirsave` is provided, intermediate results for each run are saved in `dirsave`. It is **strongly** recommended to provide `dirsave` for larger models, as parameter estimation can take hours (or even days!),and without `dirsave`, all intermediate results will be lost if something goes wrong.

Different ways to visualize the parameter estimation result can be found in the documentation.

See also [`PEtabMultistartResult`](@ref), [`get_startguesses`](@ref), and [`calibrate`](@ref).

## Keyword Arguments

  * `sampling_method = LatinHypercubeSample()`: Method for sampling a diverse (spread out) set  of starting points. See the documentation for [`get_startguesses`](@ref), which is the  function used for sampling.
  * `sample_prior::Bool = true`: See the documentation for [`get_startguesses`](@ref).
  * `seed = nothing`: Seed used when generating starting points.
  * `options = DEFAULT_OPTIONS`: Configurable options for `alg`. See the documentation for   [`calibrate`](@ref).
