```
plot3d!(S::LazySet; backend=default_polyhedra_backend(S), [alpha]=1.0,
       [color]=:blue, [colormap]=:viridis, [colorrange]=nothing,
       [interpolate]=false, [overdraw]=false, [shading]=true,
       [transparency]=true, [visible]=true)
```

三次元セットをMakieを使用してプロットします。

### 入力

入力の説明については`plot3d`を参照してください。属性と使用法の完全なリストについては、[Makieのドキュメント](http://makie.juliaplots.org/stable/plot-attributes)を参照してください。

### 注意事項

例については`plot3d`のドキュメントを参照してください。
