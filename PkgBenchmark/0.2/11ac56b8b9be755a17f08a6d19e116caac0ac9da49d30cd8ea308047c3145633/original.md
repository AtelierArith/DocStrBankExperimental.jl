Stores the results from running the benchmarks on a package.

The following (unexported) methods are defined on a `BenchmarkResults` (written below as `results`):

  * `name(results)::String` - The commit of the package benchmarked
  * `commit(results)::String` - The commit of the package benchmarked. If the package repository was dirty, the string `"dirty"` is returned.
  * `juliacommit(results)::String` - The commit of the Julia executable that ran the benchmarks
  * `benchmarkgroup(results)::BenchmarkGroup` - a [`BenchmarkGroup`](https://github.com/JuliaCI/BenchmarkTools.jl/blob/master/doc/manual.md#the-benchmarkgroup-type)  contaning the results of the benchmark.
  * `date(results)::DateTime` - The time when the benchmarks were executed
  * `benchmarkconfig(results)::BenchmarkConfig` - The [`BenchmarkConfig`](@ref) used for the benchmarks.

`BenchmarkResults` can be exported to markdown using the function [`export_markdown`](@ref).
