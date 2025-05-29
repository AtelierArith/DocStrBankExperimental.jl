```
QuantizedArray{Q<:AbstractQuantization,U<:Unsigned,D<:PreMetric,T,N} <: AbstractArray{T,N}
```

量子化配列。元の配列の「量子化」表現を表し、損失のある圧縮バージョンに相当します。

# フィールド

  * `quantizer::ArrayQuantizer{Q,U,D,T,N}` 配列の量子化
  * `data::Matrix{U}` 量子化配列の実際の圧縮表現
