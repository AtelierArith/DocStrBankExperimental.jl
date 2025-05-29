```
@benchmarkset "title" begin ... end
```

ベンチマークセットを作成します。`for` ループが提供されている場合は、複数のベンチマークセットを作成します。

!!! danger "`@benchmarkset` は非推奨です。"
    代わりに、`group = BenchmarkGroup()` に追加し、`group[key] = @benchmark...` を使用してください。


# 例

```julia
@benchmarkset "suite" for k in 1:5
    @case "case $k" rand($k, $k)
end
```
