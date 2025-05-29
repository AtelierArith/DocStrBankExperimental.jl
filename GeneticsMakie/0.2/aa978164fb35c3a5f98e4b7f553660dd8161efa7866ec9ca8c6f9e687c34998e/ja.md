```
plotld(LD::AbstractMatrix; kwargs)
plotld!(ax::Axis, LD::AbstractMatrix; kwargs)
```

対称相関行列 `LD` のヒートマップで、対角要素が x 軸に表示されます。

# キーワード引数

```
threshold       値が無視されるしきい値; デフォルト 1/9
colormap        値のカラーマップ; デフォルト cgrad(:Blues_9, 9, categorical = true)
colorrange      カラーマップの開始点と終了点; デフォルト (0, 1)
strokewidth     ヒートマップボックスの周囲のアウトラインの幅; デフォルト 0
```
