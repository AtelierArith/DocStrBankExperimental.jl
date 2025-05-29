```
M = bitinformation(A::AbstractArray{T}) where {T<:Union{Integer,AbstractFloat}}
```

配列 `A` のビット単位の相互情報量から計算されたビット単位の実情報量。オプションのキーワード引数

```
- `dim::Int=1` は次元 `dim` に沿ったビット単位の情報を計算します。
- `masked_value::T=NaN` は `A` の中で `masked_value` と等しいすべてのエントリをマスクします。
- `set_zero_insignificant::Bool=true` は重要でない情報をゼロに設定します。
- `confidence::Real=0.99` は `set_zero_insignificant` の信頼レベルです。
```
