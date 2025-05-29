```
spectraldistances(A::AbstractMatrix; [onrows=true, alpha=1.0, q=0.5])
spectraldistances(usv::SVD; [onrows=true, alpha=1.0, q=0.5])
spectraldistances(vecs::AbstactMatrix, vals::AbstractMatrix, intervals::AbstractVector{<:UnitRange})
```

スペクトル系統推論のための累積スペクトル残差距離を計算します。

`(∑_{p ∈ P} ||UₚΣₚ||₂)²`

ここで、$P$ は `getintervals` で見つかったスペクトルパーティションです。

引数:

  * A, usv: AbstractMatrix または SVD 分解 (計算前に AbstractMatrix は `svd()` に渡されます)
  * onrows: true の場合、左特異ベクトル (U 行列) に対してスペクトル距離を計算し、false の場合は右特異ベクトル (V 行列) に対して計算します
  * alpha, q: `getintervals()` に渡されます。詳細はそのドキュメントを参照してください

戻り値:

  * 距離行列

```
