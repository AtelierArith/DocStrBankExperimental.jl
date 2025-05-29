```
heatmap(A; colors)
heatmap(A, lowerleft, upperright; colors)
heatmap(xs, ys, f::Function)
```

行列 `A` に格納された値のヒートマップを、`NamedColors` のベクトル `colors` で表されるカラーマップを使用してプロットします。結果として得られる `PixelMap` を、指定された `lowerleft` および `upperright` のタプルに従って配置します（デフォルトは (0,0) と size(A) です）。

# 例

```julia-repl
julia> heatmap(0:10, 0:10, (x,y) -> x^2 + y^2)
```
