```
benchmark_result(trial::BenchmarkTools.Trial)
```

A short string with the minimum time and allocations resulting from a `BenchmarkTool.@benchmark` run.

Can be used in a testcase as:

```
trial = @benchmark myfunc($x, $y)
@test_result benchmark_result(trial)
```
