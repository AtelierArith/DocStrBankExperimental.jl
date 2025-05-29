```
getintervals_IQR(S::AbstractVector{<:Number}; alpha=1.5, ql=.25, qh=.75)
```

はスペクトルパーティションを見つけます。各後続の特異値間の対数差を計算し、デフォルトでは `1.5 * IQR(differences)` より大きい差を選択します。

つまり、分散の小さいスケールを説明するスペクトルのブレークを見つけます。

Args:

  * S: SVD因子分解の特異値
  * alpha: `q` のスカラー倍
  * q: 使用する対数差の分位数; デフォルトはQ3

Returns:

  * AbstractVector{UnitRange} Sに対応するスペクトルパーティションのインデックス
