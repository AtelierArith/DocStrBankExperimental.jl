```
Generic3D{T,V<:AbstractVector{Complex{T}},W<:AbstractVector{T},M<:AbstractMatrix{T},S} <: IsochromatSimulator{T}
```

RFおよび勾配波形を含む配列によって定義された一般的なシーケンスをシミュレートします。Generic2Dシーケンスとは異なり、励起がボクセル全体で均一であると仮定されるため、スライス方向に沿った合計は適用されません。Δtベクトルは波形の時間間隔を格納します。

# フィールド

  * `RF::V{Complex{T}}`: 各時間間隔中の（複素）RF値を持つベクトル
  * `GR::M{T}`: 各時間間隔中のGRx、GRy、およびGRz値を持つ行列
  * `sample::S`: サンプルポイントを示すBoolのベクトル
  * `Δt::V{T}`: 時間間隔を持つベクトル
