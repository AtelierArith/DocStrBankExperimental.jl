```
series(curves;
    linewidth=2,
    color=:lighttest,
    solid_color=nothing,
    labels=nothing,
    # scatter arguments, if any is set != nothing, a scatterplot is added
    marker=nothing,
    markersize=nothing,
    markercolor=automatic,
    strokecolor=nothing,
    strokewidth=nothing)
```

カーブは次のように指定できます：

  * `AbstractVector{<: AbstractVector{<: Point2}}`: 線のベクトルとしての系列のネイティブ表現
  * `AbstractMatrix`: 各行は線のy座標を表し、`x`は`1:size(curves, 1)`の範囲になります
  * `AbstractVector, AbstractMatrix`: 上記と同じですが、最初の引数がすべての線のx値を設定します
  * `AbstractVector{<: Tuple{X<: AbstractVector, Y<: AbstractVector}}`: x座標とy座標のベクトルを含むタプルのベクトル
