```
intensity(Integer, p::PointRecord)
intensity(Integer, points, inds = :)
```

ポイントレコードの「生」の強度を符号なし16ビット整数として取得します。値は、センサーの動的範囲が0から65535の範囲に対応するように正規化されるべきです。

参照: [`PointRecord`](@ref), [`color_channels`](@ref), [`return_number`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref)
