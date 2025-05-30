```
poly(vertices, indices; kwargs...)
poly(points; kwargs...)
poly(shape; kwargs...)
poly(mesh; kwargs...)
```

与えられた引数に基づいてポリゴンをプロットします。頂点とインデックスが与えられた場合、`mesh`と同様に機能します。ポイントが与えられた場合、すべてのポイントを順番に接続する1つのポリゴンを描画します。形状が与えられた場合（本質的に`GeometryBasics`によって分解可能なもの）、`decompose(shape)`をプロットします。

```
poly(coordinates, connectivity; kwargs...)
```

ポリゴンをプロットします。ポリゴンは`coordinates`（頂点の座標）と`connectivity`（頂点間のエッジ）によって定義されます。

## 属性

`AbstractPlotting.Poly`の利用可能な属性とそのデフォルトは次のとおりです：

```
  color         RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  colormap      :viridis
  colorrange    AbstractPlotting.Automatic()
  cycle         [:color => :patchcolor]
  inspectable   true
  linestyle     "nothing"
  overdraw      false
  shading       false
  strokecolor   :black
  strokewidth   0
  transparency  false
  visible       true
```
