```
benchmarkpkg(pkg, [target]::Union{String, BenchmarkConfig}; kwargs...)
```

Run a benchmark on the package `pkg` using the [`BenchmarkConfig`](@ref) or git identifier `target`. Examples of git identifiers are commit shas, branch names, or e.g. `"HEAD~1"`. Return a [`BenchmarkResults`](@ref).

The argument `pkg` can be the module of a package, a package name, or the path to the package's root directory.

**Keyword arguments**:

  * `script` - The script with the benchmarks, if not given, defaults to `benchmark/benchmarks.jl` in the package folder.
  * `postprocess` - A function to post-process results. Will be passed the `BenchmarkGroup`, which it can modify, or return a new one.
  * `resultfile` - If set, saves the output to `resultfile`
  * `retune` - Force a re-tune, saving the new tuning to the tune file.
  * `verbose::Bool = true` - Print currently running benchmark.
  * `logger_factory` - Specify the logger used during benchmark.  It is a callable object (typically a type) with no argument that creates a logger.  It must exist as a constant in some package (e.g., an anonymous function does not work).
  * `progressoptions` - Deprecated.

The result can be used by functions such as [`judge`](@ref). If you choose to, you can save the results manually using [`writeresults`](@ref) where `results` is the return value of this function. It can be read back with [`readresults`](@ref).

**Example invocations:**

```julia
using PkgBenchmark

import MyPkg
benchmarkpkg(MyPkg) # run the benchmarks at the current state of the repository
benchmarkpkg(MyPkg, "my-feature") # run the benchmarks for a particular branch/commit/tag
benchmarkpkg(MyPkg, "my-feature"; script="/home/me/mycustombenchmark.jl")
benchmarkpkg(MyPkg, BenchmarkConfig(id = "my-feature",
                                            env = Dict("JULIA_NUM_THREADS" => 4),
                                            juliacmd = `julia -O3`))
benchmarkpkg(MyPkg,  # Run the benchmarks and divide the (median of) results by 1000
    postprocess=(results)->(results["g"] = median(results["g"])/1_000)
```
