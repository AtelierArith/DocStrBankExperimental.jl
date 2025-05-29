```
push!(meas::TimeSeries, single_value::Number)
```

`push!` を使用して、データストリームに単一の数値を追加します。現在のデータストリームが満杯である場合、つまり `length(meas.datastream) == meas.current_index` の場合、値が追加されるとデータストリームは `resize!` されます。これにより `O(n)` の複雑性が生じる可能性があります。
