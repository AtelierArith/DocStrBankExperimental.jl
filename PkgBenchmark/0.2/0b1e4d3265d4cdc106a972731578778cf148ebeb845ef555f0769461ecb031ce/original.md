```
BenchmarkConfig(;id::Union{String, Nothing} = nothing,
                 juliacmd::Cmd = `joinpath(Sys.BINDIR, Base.julia_exename())`,
                 env::Dict{String, Any} = Dict{String, Any}())
```

A `BenchmarkConfig` contains the configuration for the benchmarks to be executed by [`benchmarkpkg`](@ref).

This includes the following:

  * The commit of the package the benchmarks are run on.
  * What julia command should be run, i.e. the path to the Julia executable and

the command flags used (e.g. optimization level with `-O`).

  * Custom environment variables (e.g. `JULIA_NUM_THREADS`).

The constructor takes the following keyword arguments:

  * `id` - A git identifier like a commit, branch, tag, "HEAD", "HEAD~1" etc.        If `id == nothing` then benchmark will be done on the current state        of the repo (even if it is dirty).
  * `juliacmd` - Used to execute the benchmarks, defaults to the julia executable              that the Pkgbenchmark-functions are called from. Can also include command flags.
  * `env` - Contains custom environment variables that will be active when the         benchmarks are run.

# Examples

```julia
julia> using Pkgbenchmark

julia> BenchmarkConfig(id = "performance_improvements",
                       juliacmd = `julia -O3`,
                       env = Dict("JULIA_NUM_THREADS" => 4))
BenchmarkConfig:
    id: performance_improvements
    juliacmd: `julia -O3`
    env: JULIA_NUM_THREADS => 4
```
