```
decode(geohash, bits_per_char = 2)
```

指定された `bits_per_char` で `geohash` 文字列を与えると、対応する geohash セルの中心の座標をタプル `(lon, lat)` として返します。

参照: [`decode_exactly`](@ref)
