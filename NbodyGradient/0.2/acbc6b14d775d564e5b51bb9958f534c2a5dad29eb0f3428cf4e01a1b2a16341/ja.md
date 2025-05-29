```
TransitTiming{T<:AbstractFloat} <: TransitOutput{T}
```

輸送時間と導関数。

# (ユーザー向け) フィールド

  * `tt::Matrix{T}` : 各天体の輸送時間。
  * `dtdq0::Array{T,4}` : 初期デカルト座標および質量に対する輸送時間の導関数。
  * `dtdelements::Array{T,4}` : 初期軌道要素および質量に対する輸送時間の導関数。
