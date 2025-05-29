```
judge(target::BenchmarkResults, baseline::BenchmarkResults, f;
      judgekwargs = Dict())
```

Judges the two [`BenchmarkResults`](@ref) in `target` and `baseline` using the function `f`.

**Return value**

Returns a [`BenchmarkJudgement`](@ref)
