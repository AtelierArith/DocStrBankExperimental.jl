```
parker_weight(rg::SinoGeom, T = Float32)
```

360°以外の軌道に対するパーカー重み付けを計算します。詳細は https://doi.org/10.1118/1.595078 を参照してください。返されるのは次のサイズの `Matrix{T}` です：

  * 通常の180または360軌道の `SinoPar` に対して (1,1)
  * 異常な軌道の `SinoPar` に対して (1,na)
  * 通常の360軌道の `SinoFan` に対して (1,1)
  * 通常の360軌道の `SinoFan` に対して (ns,na)
