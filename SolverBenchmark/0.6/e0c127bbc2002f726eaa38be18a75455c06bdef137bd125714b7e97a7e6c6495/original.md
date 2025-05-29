```
posted_gist = to_gist(results)
```

Create and post a gist with the benchmark results and performance profiles.

Inputs:

  * `results::BenchmarkResults`: the result of `PkgBenchmark.benchmarkpkg`

Output:

  * the return value of GitHub.jl's `create_gist`.
