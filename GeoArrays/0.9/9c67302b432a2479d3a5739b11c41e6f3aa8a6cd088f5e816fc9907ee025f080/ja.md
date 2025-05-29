```
function crop(ga::GeoArray, cbox::NamedTuple{(:min_x, :min_y, :max_x, :max_y),Tuple{Float64,Float64,Float64,Float64}})
```

入力GeoArrayを座標（ボックスまたは別のGeoArray）でクロップします。座標範囲がGeoArrayより大きい場合、結果には重なっている部分のみが含まれます。
