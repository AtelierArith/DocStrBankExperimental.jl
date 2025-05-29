```
modulusfunction(data::RheoFreqData, Gp::T1, Gpp::T2) where {T1<:Function, T2<:Function}
modulusfunction(Gp::T1, Gpp::T2, data::RheoFreqData) where {T1<:Function, T2<:Function}
```

与えられた関数 `Gp` と `Gpp` を使用して計算された弾性率を持つ新しい `RheoFreqData` を返します。これは、入力 `data` に存在する周波数値に適用されます。

通常、`frequencyspec` 関数を使用して生成された `RheoFreqData` と共に使用されます。
