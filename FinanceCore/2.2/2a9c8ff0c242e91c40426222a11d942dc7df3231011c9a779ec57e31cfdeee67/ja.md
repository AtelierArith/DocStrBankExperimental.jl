```
present_value(yield_model, cashflows[, timepoints=pairs(cashflows)])
```

指定された `yield_model` で `cashflows` ベクトルを割引し、`timepoints` で指定された時点でキャッシュフローが発生します。`timepoints` が指定されていない場合、キャッシュフローはキャッシュフローのインデックスで発生すると仮定します。

もしあなたの `timepoints` が日付であれば、DayCounts.jl を使用して時間間隔の浮動小数点表現に変換できます。

# 例

```julia-repl
julia> present_value(0.1, [10,20],[0,1])
28.18181818181818
julia> present_value(Continuous(0.1), [10,20],[0,1])
28.096748360719193
julia> present_value(Continuous(0.1), [10,20],[1,2])
25.422989241919232
julia> present_value(Continuous(0.1), [10,20])
25.422989241919232
```
