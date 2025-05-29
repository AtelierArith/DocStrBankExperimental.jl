```
intensity(p::PointRecord)
intensity(points, inds = :)
```

パルスの強度を取得し、センサーのダイナミックレンジが0から1の範囲で表されるように正規化します。

関連情報: [`PointRecord`](@ref), [`color_channels`](@ref), [`return_number`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref)
