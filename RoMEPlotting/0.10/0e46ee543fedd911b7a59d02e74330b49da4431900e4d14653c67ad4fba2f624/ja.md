```julia
plotUpMsgsAtCliq(treel, cllb, lb; show, w, h, levels, dims)

```

クリーク `cllb::Symbol` から変数 `lb::Symbol` への上向き信念を描画します。

例:

```julia
plotUpMsgsAtCliq(tree, :x2, :x1)
```

関連

plotKDE, getUpMsgs
