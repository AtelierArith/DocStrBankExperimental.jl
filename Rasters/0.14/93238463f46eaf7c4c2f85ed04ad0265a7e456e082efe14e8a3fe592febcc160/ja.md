```
cellarea([method], x)
```

`x`の各グリッドセルの近似面積を返します。地球を球体と仮定することで、緯度に応じて真のサイズを約0.1%程度に近似します。

このメソッドを完全に利用するには、`using ArchGDAL`または`using Proj`を実行してください。

  * `method`: 投影の平面で面積を計算するか、半径のある球体上で計算するかを指定できます。`Planar()`またはデフォルトの`Spherical(; radius=...)`を使用します。
  * `Spherical`は、すべての点を経度緯度に戻すことによって球体上のセル面積を計算します。ここで`radius`キーワード引数を使用して半径を指定できます。デフォルトでは、これは地球の平均半径である`6371008.8`です。
  * `Planar`は、選択したCRSの平面でセル面積を計算します。非等面積投影の場合、これはおそらく不正確であることに注意してください。

入力と同じxおよびy次元を持つRasterを返し、ラスタ内の各値はセルの面積（デフォルトではメートル単位）をエンコードします。

## 例

```julia
using Rasters, Proj, Rasters.Lookups
xdim = X(Projected(90.0:10.0:120; sampling=Intervals(Start()), crs=EPSG(4326)))
ydim = Y(Projected(0.0:10.0:50; sampling=Intervals(Start()), crs=EPSG(4326)))
myraster = rand(xdim, ydim)
cs = cellarea(myraster)

# 出力
╭───────────────────────╮
│ 4×6 Raster{Float64,2} │
├───────────────────────┴─────────────────────────────────────────────────── dims ┐
  ↓ X Projected{Float64} 90.0:10.0:120.0 ForwardOrdered Regular Intervals{Start},
  → Y Projected{Float64} 0.0:10.0:50.0 ForwardOrdered Regular Intervals{Start}
├───────────────────────────────────────────────────────────────────────── raster ┤
  extent: Extent(X = (90.0, 130.0), Y = (0.0, 60.0))

  crs: EPSG:4326
└─────────────────────────────────────────────────────────────────────────────────┘
   ↓ →  0.0        10.0        20.0        30.0            40.0      50.0
  90.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
 100.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
 110.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
 120.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
```

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、githubの問題を報告してください。
