Stores the results from running a judgement, see [`judge`](@ref).

The following (unexported) methods are defined on a `BenchmarkJudgement` (written below as `judgement`):

  * `target_result(judgement)::BenchmarkResults` - the [`BenchmarkResults`](@ref) of the `target`.
  * `baseline_result(judgement)::BenchmarkResults` -  the [`BenchmarkResults`](@ref) of the `baseline`.
  * `benchmarkgroup(judgement)::BenchmarkGroup` - a [`BenchmarkGroup`](https://github.com/JuliaCI/BenchmarkTools.jl/blob/master/doc/manual.md#the-benchmarkgroup-type)  containing the estimated results

A `BenchmarkJudgement` can be exported to markdown using the function [`export_markdown`](@ref).

See also [`BenchmarkResults`](@ref)
