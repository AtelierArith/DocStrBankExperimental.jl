```
convert_coords(eco, i::Int64, width::Int64)
convert_coords(eco, x::Int64, y::Int64, width::Int64)
```

座標を二次元（`x`,`y`）形式から一次元（`i`）形式に変換する関数、またはその逆を、グリッドの`width`を使用して行います。この関数は座標の配列にも適用できます。
