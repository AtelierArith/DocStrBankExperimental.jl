```
      vectorsample(grid::ExtendableGrid{Tv, Ti}, v;
                  offset = :default,
                  rasterpoints = 15,
                  reltol = 1.0e-10,
                  gridscale = 1.0,
                  xlimits = (1, -1),
                  ylimits = (1, -1),
                  zlimits = (1, -1)) where {Tv, Ti}
```

与えられたベクトル場の値を抽出します（ピースワイズ線形ベクトル場のノード値または与えられた一般化バリセントリック座標に対するベクトル場の評価を提供するコールバック関数）。`offset + i * spacing` のすべてのサンプリングポイントで、i は Z^d であり、タプルの offset と spacing によって定義されます。返された値は [`quiverdata`](@ref) に供給できます。

デフォルトでは、offset はグリッド座標の最小値にあり、spacing は最大のグリッド拡張を 10 で割ったものとして定義されます。

将来のバージョンでは、中間の `rasterflux` を使用してストリームラインを計算できます。

このコードは 3D に対応しています。
