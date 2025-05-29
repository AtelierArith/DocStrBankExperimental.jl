```
@case title <expr to benchmark> [setup=<setup expr>]
```

Mark an expression as a benchmark case. Must be used inside [`@benchmarkset`](@ref).

!!! danger "`@benchmarkset` is deprecated."
    Instead, add to `group = BenchmarkGroup()` using `group[key] = @benchmark...`

