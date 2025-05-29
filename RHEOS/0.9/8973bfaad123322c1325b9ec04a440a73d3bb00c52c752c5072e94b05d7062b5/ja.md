```
RheoFreqData(Gp::Vector{T1}, Gpp::Vector{T2}, ω::Vector{T3}, log::OrderedDict{Any,Any}) where {T1<:Real, T2<:Real, T3<:Real}
```

`RheoFreqData` は貯蔵弾性率、損失弾性率および周波数データを含みます。

好ましい場合は、正しい順序で3つのデータベクターを提供することによって、インスタンスを手動で生成することができます。

# フィールド

  * `Gp`: 貯蔵弾性率
  * `Gpp`: 損失弾性率
  * `ω`: 周波数
  * `log`: 構造体のイベントのログ、例：前処理
