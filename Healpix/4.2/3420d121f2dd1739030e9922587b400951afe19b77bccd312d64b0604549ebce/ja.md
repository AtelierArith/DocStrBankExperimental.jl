```
ang2pix{T, O, AA}(map::HealpixMap{T, O}, theta, phi)
ang2pix{T, O, AA}(map::PolarizedHealpixMap{T, O}, theta, phi)
```

コラテュード `theta` (∈ [0, π]) とロングイチュード `phi` (∈ [0, 2π]) で指定された方向を Healpix マップ `map` のピクセルのインデックスに変換します。
