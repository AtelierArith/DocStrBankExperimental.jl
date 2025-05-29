```
PkgBenchmark(; file="~/.julia/packages/PkgTemplates/MepaC/templates/benchmark/benchmarks.jlt")
```

Sets up a [PkgBenchmark.jl](https://github.com/JuliaCI/PkgBenchmark.jl) benchmark suite.

To ensure benchmark reproducibility, you will need to manually create an environment in the `benchmark` subfolder (for which the `Manifest.toml` is committed to version control). In this environment, you should at the very least:

  * `pkg> add BenchmarkTools`
  * `pkg> dev` your new package.

## Keyword Arguments

  * `file::AbstractString`: Template file for `benchmarks.jl`.
