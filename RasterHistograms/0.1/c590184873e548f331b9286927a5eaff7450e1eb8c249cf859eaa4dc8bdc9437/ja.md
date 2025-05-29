```
function volume_weights(rs::Union{Raster, RasterStack}; equator_one_degree = 111e3)
```

`Raster`または`RasterStack`内の各グリッドセルの体積から計算された`Histogram`のための`Weights`を返します。モデルの解像度は`Raster`または`RasterStack`の`X`および`Y`次元から推測され、`X`および`Y`に沿って解像度が一意であると仮定されます（ただし、`X`と`Y`で異なる場合があります）。キーワード引数`equator_one_degree`は、赤道での1度をメートル単位で表したものです。この関数はコンテナ`Weights`を返すため、`fit(::Histogram)`関数に直接渡すことができます。
