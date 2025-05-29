```
@benchmarkset "title" begin ... end
```

Create a benchmark set, or multiple benchmark sets if a `for` loop is provided.

!!! danger "`@benchmarkset` is deprecated."
    Instead, add to `group = BenchmarkGroup()` using `group[key] = @benchmark...`


# Examples

```julia
@benchmarkset "suite" for k in 1:5
    @case "case $k" rand($k, $k)
end
```
