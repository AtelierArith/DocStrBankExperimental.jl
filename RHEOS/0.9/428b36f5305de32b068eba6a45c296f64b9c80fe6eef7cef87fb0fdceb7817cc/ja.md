```
stressfunction(data::RheoTimeData, f::T) where T<:Function
stressfunction(f::T, data::RheoTimeData) where T<:Function
```

パラメータデータの時間データに関数 `f` を適用することで計算された応力値を持つ新しい `RheoTimeData` を返します。

通常、`timeline` 関数を使用して生成された `RheoTimeData` と共に使用されます。
