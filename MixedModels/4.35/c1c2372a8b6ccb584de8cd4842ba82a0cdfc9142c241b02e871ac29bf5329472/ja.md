```
LinearMixedModel
```

線形混合効果モデルの表現

## フィールド

  * `formula`: モデルのための式
  * `reterms`: ランダム効果項の `Vector{AbstractReMat{T}}`。
  * `Xymat`: フルランクの固定効果モデル行列 `X` と応答 `y` の水平結合を `FeMat{T}` として表現
  * `feterm`: 固定効果モデル行列を `FeTerm{T}` として表現
  * `sqrtwts`: ケースの重みの平方根のベクトル。空であることも可能。
  * `parmap` : θ を λ にマッピングする (block, row, column) の `Vector{NTuple{3,Int}}`
  * `dims` : 次元の `NamedTuple{(:n, :p, :nretrms),NTuple{3,Int}}`。 `p` は `X` のランクであり、`size(X, 2)` より小さい場合があります。
  * `A`: `hcat(Z,X,y)'hcat(Z,X,y` の行優先でパックされた下三角行列を含む `Vector{AbstractMatrix}`
  * `L`: `Λ'AΛ+I` のブロック下Cholesky因子で、`A` と同じベクトル表現
  * `optsum`: [`OptSummary`](@ref) オブジェクト

## プロパティ

  * `θ` または `theta`: λ を形成するために使用される共分散パラメータベクトル
  * `β` または `beta`: 固定効果係数ベクトル
  * `λ` または `lambda`: `Λ` の対角ブロックに繰り返される下三角行列のベクトル
  * `σ` または `sigma`: 観測ごとのノイズの標準偏差の現在の値
  * `b`: 元のスケールでのランダム効果、行列のベクトルとして
  * `u`: 直交スケールでのランダム効果、行列のベクトルとして
  * `lowerbd`: θ の要素の下限
  * `X`: 固定効果モデル行列
  * `y`: 応答ベクトル
