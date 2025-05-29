```
judge(target::BenchmarkResults, baseline::BenchmarkResults, f;
      judgekwargs = Dict())
```

`target` と `baseline` の二つの [`BenchmarkResults`](@ref) を関数 `f` を使用して評価します。

**戻り値**

[`BenchmarkJudgement`](@ref) を返します。
