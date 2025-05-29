```
getintervals(S::AbstractVector{<:Number}; alpha=1.0, q=0.5)
```

はスペクトルパーティションを見つけます。各後続の特異値間の対数差を計算し、デフォルトでは `1.0 * Q2(differences)` より大きい差を選択します。

つまり、分散の小さいスケールを説明するスペクトルのブレークを見つけます。

引数:

  * S: SVD因子分解の特異値
  * alpha: `q` のスカラー倍
  * q: 使用する対数差の分位数; デフォルトは Q2

戻り値:

  * AbstractVector{UnitRange} S に対応するスペクトルパーティションのインデックス
