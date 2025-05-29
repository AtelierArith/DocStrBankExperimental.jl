```
T, Q = skew_tridiagonalize(A::AbstractMatrix{T}; overwrite_a=false, calc_q=true) where {T<:Number}
```

または

```
T = skew_tridiagonalize(A::AbstractMatrix{T}; overwrite_a=false, calc_q=false) where {T<:Number}
```

実数または複素数のスキュー対称行列 (A=-A^T) を対角成分がゼロの三重対角行列 T に変換し、A = Q T Q^T となるような直交行列 (実数の場合) またはユニタリ行列 (複素数の場合) U を得ます (Q^T であり、複素数の場合でも Q^dagger ではないことに注意してください)。

overwrite*a=true の場合、A は上書きされ、calc*q=true の場合のみ Q が計算されます (デフォルト: true)。
