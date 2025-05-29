```
return_count([T], p::PointRecord)
return_count([T], points, inds = :)
```

レーザーパルスによって生成されたリターンの総数を取得します。この値は、PDRF 6–10の場合は1から15の間、レガシーPDRF 0–5の場合は1から5の間です。

参照: [`PointRecord`](@ref), [`intensity`](@ref), [`return_number`](@ref), [`waveform_packet`](@ref)
