```
flowerplot!(ax, bm)
flowerplot(bm)
```

ブロックモデルグループに従って円の中にノードを配置したネットワークをプロットします。最初のグループは中央に配置されます。

# 属性

  * `edgecolor = :grey70`
  * `edgewidth = 1`
  * `nodecolor = :black`
  * `showlabels = true`
  * `radii = fill(1, length(bm.labels))`
  * `args...` さらなる引数は `Makie.scatter` に渡されます。
