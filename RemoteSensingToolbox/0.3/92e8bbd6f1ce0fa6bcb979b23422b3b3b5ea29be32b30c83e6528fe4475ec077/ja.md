```
color_infrared(src::AbstractSatellite; lower=0.02, upper=0.98)
color_infrared(s::Type{AbstractSatellite}, raster::AbstractRasterStack; lower=0.02, upper=0.98)
```

衛星画像をカラー赤外線バンドの組み合わせを使用して視覚化します。これにより、植生が赤で、水が青で、都市部が灰色で強調表示されます。

`AbstractSatellite` または `Type{AbstractSatellite}` と `AbstractRasterStack` の組み合わせのいずれかを受け入れます。

`RGB{N0f8}` または `Gray{N0f8}` 要素の `Array` を返します。

# キーワード

  * `lower`: 画像のヒストグラムを調整するために使用する下位パーセンタイル。
  * `upper`: 画像のヒストグラムを調整するために使用する上位パーセンタイル。
