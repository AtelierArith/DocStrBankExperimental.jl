```
combine_covariance_matrices(
    vect::Vector{CovarianceMatrix{T}},
    cor_weights::Vector{<:Real} = repeat([1.0], length(vect)),
    vol_weights::Vector{<:Real} = cor_weights,
    time_period_per_unit::Union{Missing,Dates.Period} = vect[1].time_period_per_unit,
) where T<:Real
```

`CovarianceMatrix` 構造体のベクトルを1つの `CovarianceMatrix` 構造体に結合します。

### 入力

  * `vect` - `CovarianceMatrix` 構造体のベクトル。
  * `cor_weights` - 各共分散行列からの相関をどの程度重視するかのベクトル（デフォルトでは等重み付けされます）。
  * `vol_weights` - 各共分散行列からのボラティリティをどの程度重視するかのベクトル（デフォルトでは等重み付けされます）。
  * `time_period_per_unit` - ボラティリティをどの時間単位にスケーリングするか。

### 戻り値

  * 行列と、行/列ごとのラベルのベクトル。
