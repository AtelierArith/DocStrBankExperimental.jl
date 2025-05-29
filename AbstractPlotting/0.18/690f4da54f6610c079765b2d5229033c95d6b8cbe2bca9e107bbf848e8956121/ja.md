```
poly(vertices, indices; kwargs...)
poly(points; kwargs...)
poly(shape; kwargs...)
poly(mesh; kwargs...)
```

与えられた引数に基づいて多角形をプロットします。頂点とインデックスが与えられた場合、`mesh`と同様に機能します。ポイントが与えられた場合、すべてのポイントを順番に接続する1つの多角形を描画します。形状が与えられた場合（本質的に`GeometryBasics`によって分解可能なもの）、`decompose(shape)`をプロットします。

```
poly(coordinates, connectivity; kwargs...)
```

多角形をプロットします。これは`coordinates`（頂点の座標）と`connectivity`（頂点間のエッジ）によって定義されます。

## 属性

`AbstractPlotting.Combined{AbstractPlotting.poly!}`の利用可能な属性とそのデフォルトは次のとおりです：

```

```
