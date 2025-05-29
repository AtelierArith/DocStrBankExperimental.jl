```
waveform_packet(p::PointRecord)
waveform_packet(points, inds = :)
```

PDRF 4/5/9/10 のポイントレコードの生波形パケットを取得します。波形パケットが含まれていない場合は `missing` を返します。PointClouds.jl は現在、波形データを扱うための機能が非常に限られています。

参照: [`PointRecord`](@ref), [`intensity`](@ref), [`return_number`](@ref), [`return_count`](@ref)
