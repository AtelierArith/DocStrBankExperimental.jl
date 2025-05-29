```
pix2ang{T, O <: Order}(map::HealpixMap{T, O}, ipix) -> (Float64, Float64)
pix2ang{T, O <: Order}(map::PolarizedHealpixMap{T, O}, ipix) -> (Float64, Float64)
```

インデックス `ipix` のピクセル中心の方向の緯度 `theta` と経度 `phi` のペアを返します。ここで、`theta` はコラテュード、`phi` は経度です。
