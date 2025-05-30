```
agriculture(src::AbstractSatellite; lower=0.02, upper=0.98)
agriculture(s::Type{AbstractSatellite}, raster::AbstractRasterStack; lower=0.02, upper=0.98)
```

農業バンドの組み合わせを使用して衛星画像を視覚化します。これは作物のモニタリングに使用され、健康な植生を強調します。

`AbstractSatellite` または `Type{AbstractSatellite}` と `AbstractRasterStack` の組み合わせのいずれかを受け入れます。

`RGB{N0f8}` または `Gray{N0f8}` 要素の `Array` を返します。

# キーワード

  * `lower`: 画像のヒストグラムを調整するために使用する下位パーセンタイル。
  * `upper`: 画像のヒストグラムを調整するために使用する上位パーセンタイル。
