```
geology(src::AbstractSatellite; lower=0.02, upper=0.98)
geology(s::Type{AbstractSatellite}, raster::AbstractRasterStack; lower=0.02, upper=0.98)
```

地質バンドの組み合わせで衛星画像を視覚化し、地質構造、岩石の特徴、断層を強調します。

`AbstractSatellite` または `Type{AbstractSatellite}` と `AbstractRasterStack` の組み合わせのいずれかを受け入れます。

`RGB{N0f8}` または `Gray{N0f8}` 要素の `Array` を返します。

# キーワード

  * `lower`: 画像のヒストグラムを調整するために使用する下位パーセンタイル。
  * `upper`: 画像のヒストグラムを調整するために使用する上位パーセンタイル。
