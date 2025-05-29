```
export_markdown(file::String, results::BenchmarkResults)
export_markdown(io::IO,       results::BenchmarkResults)
export_markdown(file::String, results::BenchmarkJudgement; export_invariants=false)
export_markdown(io::IO,       results::BenchmarkJudgement; export_invariants=false)
```

Writes the `results` to `file` or `io` in markdown format.

When exporting a `BenchmarkJudgement`, by default only the results corresponding to possible regressions or improvements will be included. To also export the invariant results, set `export_invariants=true`.

See also: [`BenchmarkResults`](@ref), [`BenchmarkJudgement`](@ref)
