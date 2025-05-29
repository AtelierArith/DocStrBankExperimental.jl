```
decode_exactly(geohash, bits_per_char)
```

指定された `bits_per_char` で `geohash` 文字列を与えると、対応する geohash セルの中心の座標と誤差範囲をタプル `(lon, lat, lon_err, lat_err)` として返します。つまり、対応するセル内の各点は、経度が `lon` ± `lon_err` の範囲内にあり、緯度も同様です。

参照: [`rectangle`](@ref)
