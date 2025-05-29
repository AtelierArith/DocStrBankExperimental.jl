```
benchmark(package_specs::Union{PackageSpec,Vector{PackageSpec}}; output_dir::String=".", script::Union{String,Nothing}=nothing, tune::Bool=false, exeflags::Cmd=``, extra_pkgs::Vector{String}=String[])
```

Run benchmarks for a given Julia package.

This function runs the benchmarks specified in the `script` for the package defined by the `package_spec`. If `script` is not provided, the function will use the default benchmark script located at `{PACKAGE_SRC_DIR}/benchmark/benchmarks.jl`.

The benchmarks are run using the `SUITE` variable defined in the benchmark script, which should be of type BenchmarkTools.BenchmarkGroup. The benchmarks can be run with or without tuning depending on the value of the `tune` argument.

The results of the benchmarks are saved to a JSON file named `results_packagename@rev.json` in the specified `output_dir`.

# Arguments

  * `package::Union{PackageSpec,Vector{PackageSpec}}`: The package specification containing information about the package for which to run the benchmarks. You can also pass a vector of package specifications to run benchmarks for multiple versions of a package.
  * `output_dir::String="."`: The directory where the benchmark results JSON file will be saved (default: current directory).
  * `script::Union{String,Nothing}=nothing`: The path to the benchmark script file. If not provided, the default script at `{PACKAGE}/benchmark/benchmarks.jl` will be used.
  * `tune::Bool=false`: Whether to run benchmarks with tuning (default: false).
  * `exeflags::Cmd=```: Additional execution flags for running the benchmark script (default: empty).
  * `extra_pkgs::Vector{String}=String[]`: Additional packages to add to the benchmark environment.
  * `benchmark_on::Union{String,Nothing}=nothing`: If the benchmark script file is to be downloaded, this specifies the revision to use.
  * `filter_benchmarks::Vector{String}=String[]`: Filter the benchmarks to run (default: all).
  * `nsamples_load_time::Int=5`: Number of samples to take for the time-to-load benchmark.
