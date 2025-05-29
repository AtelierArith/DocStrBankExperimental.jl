```
tune!(group::BenchmarkGroup; verbose::Bool = false, pad = "", kwargs...)
```

Tune a `BenchmarkGroup` instance. For most benchmarks, `tune!` needs to perform many evaluations to determine the proper parameters for any given benchmark - often more evaluations than are performed when running a trial. In fact, the majority of total benchmarking time is usually spent tuning parameters, rather than actually running trials.
