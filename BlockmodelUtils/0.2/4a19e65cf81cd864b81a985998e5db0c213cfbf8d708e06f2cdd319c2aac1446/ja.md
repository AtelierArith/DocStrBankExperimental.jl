```
densityplot!(ax, bm)
densityplot(bm)
```

ブロック密度行列をヒートマップとしてプロットします。

# 属性

  * `xticklabels = bm.labels`
  * `yticklabels = bm.labels`
  * `rotate_xlabels` = false
  * `kwargs...` は `Makie.heatmap` に渡されます
