```
@case title <expr to benchmark> [setup=<setup expr>]
```

式をベンチマークケースとしてマークします。[`@benchmarkset`](@ref)の中で使用する必要があります。

!!! danger "`@benchmarkset`は非推奨です。"
    代わりに、`group = BenchmarkGroup()`に追加し、`group[key] = @benchmark...`を使用してください。

