```
pix2angRing(resol::Resolution, pixel) -> (Float64, Float64)
```

Healpixマップのリング順におけるピクセルの（1ベースの）インデックスが与えられたとき、その中心に対応する（`colatitude`、`longitude`）角度のペアを返します。両方の角度はラジアンで表現されます。
