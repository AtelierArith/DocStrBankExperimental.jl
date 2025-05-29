```
densityplot!(ax, bm)
densityplot(bm)
```

Plot the block density matrix as a heatmap.

# Attributes

  * `xticklabels = bm.labels`
  * `yticklabels = bm.labels`
  * `rotate_xlabels` = false
  * `kwargs...` are passed to `Makie.heatmap`
