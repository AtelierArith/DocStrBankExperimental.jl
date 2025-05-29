```
judge(pkg::Union{Module, String},
      [target]::Union{String, BenchmarkConfig},
      baseline::Union{String, BenchmarkConfig};
      kwargs...)
```

**Arguments**:

  * `pkg` - Package to benchmark. Either a package module, name, or directory.
  * `target` - What do judge, given as a git id or a [`BenchmarkConfig`](@ref). If skipped, use the current state of the package repo.
  * `baseline` - The commit / [`BenchmarkConfig`](@ref) to compare `target` against.

**Keyword arguments**:

  * `f` - Estimator function to use in the [judging](https://github.com/JuliaCI/BenchmarkTools.jl/blob/master/doc/manual.md#trialratio-and-trialjudgement).
  * `judgekwargs::Dict{Symbol, Any}` - keyword arguments to pass to the `judge` function in BenchmarkTools

The remaining keyword arguments are passed to [`benchmarkpkg`](@ref)

**Return value**:

Returns a [`BenchmarkJudgement`](@ref)
