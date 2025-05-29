```
IVFADCIndex{U<:Unsigned, I<:Unsigned, Dc<:Distances.PreMetric, Dr<:Distances.PreMetric, T<:AbstractFloat, Q<:AbstractCoarseQuantizer{Dc,T}}
```

逆ファイルシステムオブジェクトです。含まれているベクトルへの近似最近傍検索を可能にします。

# フィールド

  * `coarse_quantizer::AbstractCoarseQuantizer{Dc,T}` は粗いベクトルを含みます
  * `residual_quantizer::QuantizedArrays.OrthogonalQuantizer{U,Dr,T,2}`

インデックスに追加する際にベクトルを量子化するために使用されます

  * `inverse_index::InvertedIndex{I,U}` は実際に使用される逆インデックスです

検索を実行するために。
