```
push!(meas::TimeSeries, value)
```

`push!` 可能な多くの `value` を [`TimeSeries`] `datastream` に追加します。

# 追加情報

値が十分に長い場合、これにより `datastream` が `resize!` され、`O(n)` の複雑さを持つ可能性があります。必要なメモリを事前に割り当てることが推奨されます [`TimeSeries`](@ref)`(name, size)`。
