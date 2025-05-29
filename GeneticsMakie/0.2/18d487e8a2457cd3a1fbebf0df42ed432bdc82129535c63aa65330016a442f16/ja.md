```
plotrg(r::AbstractMatrix)
plotrg!(ax::Axis, r::AbstractMatrix)
```

行列 `r` の相関プロット。

# キーワード引数

```
circle          矩形の代わりに円を描画するかどうか; デフォルトは true
diagonal        対角要素を視覚化するかどうか; デフォルトは false
colormap        値のカラーマップ; デフォルトは :RdBu_10
colorrange      カラーマップの開始点と終了点; デフォルトは (-1, 1)
strokewidth     周囲のボックスのアウトラインの幅; デフォルトは 0.5
```
