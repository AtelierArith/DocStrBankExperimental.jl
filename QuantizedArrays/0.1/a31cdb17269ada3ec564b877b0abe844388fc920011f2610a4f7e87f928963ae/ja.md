```
ArrayQuantizer{Q,U,D,T,N}
```

配列量子化器オブジェクトです。これは、型 `T` の要素を持つ配列を、型 `U` の要素を持つ「量子化された」バージョンに変換します。

# フィールド

  * `quantization::Q` 使用される量子化のタイプ、すなわち加法的、直交的
  * `dims::NTuple{N,Int}` 元の配列の次元
  * `codebooks::Vector{CodeBook{U,T}}` コードブック
  * `k::Int` 各コードブック内のベクトルプロトタイプの数
  * `distance::D` 使用される距離
  * `rot::Matrix{T}` 回転行列
