```
Generic2D{T,V,M,S} where {T<:AbstractFloat, V<:AbstractVector, M<:AbstractMatrix, S} <: IsochromatSimulator{T}
```

RFおよび勾配波形を含む配列によって定義された一般的な2Dシーケンスをシミュレートします。スライスプロファイル効果を考慮するためにz位置に対するループが含まれています。Δtベクトルは波形の時間間隔を格納します。

# フィールド

  * `RF::V{Complex{T}}`: 各時間間隔中の（複素）RF値を持つベクトル
  * `GR::M{T}`: 各時間間隔中のGRx、GRy、およびGRz値を持つ行列
  * `sample::S`: サンプルポイントを示すBoolのベクトル
  * `Δt::V{T}`: 時間間隔を持つベクトル
  * `z::V{T}`: スライス方向に沿った異なる位置を持つベクトル
