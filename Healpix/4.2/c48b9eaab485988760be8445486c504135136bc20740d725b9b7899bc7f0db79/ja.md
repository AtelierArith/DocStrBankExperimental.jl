```
pix2angNest(resol::Resolution, pixel) -> (Float64, Float64)
```

与えられた（1ベースの）ピクセルのインデックスがネストされた順序のHealpixマップにおいて、その中心に対応する（`colatitude`、`longitude`）角度のペアを返します。両方の角度はラジアンで表現されます。
