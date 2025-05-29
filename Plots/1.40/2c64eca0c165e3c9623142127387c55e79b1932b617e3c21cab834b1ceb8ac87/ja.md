```
hexbin(x,y)
hexbin!(x,y)
```

六角形ビニングプロットを作成します（六角形のビンを持つ観測値 `(x[i],y[i])` のヒストグラム）。

# 例

```julia-repl
julia> hexbin(randn(10_000), randn(10_000))
```
