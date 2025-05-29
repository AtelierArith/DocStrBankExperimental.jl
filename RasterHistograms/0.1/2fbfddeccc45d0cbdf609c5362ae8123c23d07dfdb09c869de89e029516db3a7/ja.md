```
function area_weights(rs::Union{Raster, RasterStack}; equator_one_degree = 111e3)
```

`Raster`または`RasterStack`内の各グリッドセルの面積から計算された`Histogram`のための`Weights`を返します。`Raster`または`RasterStack`は、面積重みを見たい次元に沿って最初にスライスする必要があります。例えば、海面での面積重みの場合、関数には`rs[Z(1)]`を渡す必要があります。元の`Raster`が2つの空間次元しか持たない場合、このステップはスキップできます。キーワード引数`equator_one_degree`は、赤道での1度のメートル単位の長さです。この関数は`Weights`というコンテナを返すため、`fit(::Histogram)`関数に直接渡すことができます。
