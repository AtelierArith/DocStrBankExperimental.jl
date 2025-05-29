```
return_number([T], p::PointRecord)
return_number([T], points, inds = :)
```

レーザーパルスのどのリターンがポイントデータレコードを生成したかを取得します。値は、PDRF 6–10の場合は1から15の間、レガシーPDRF 0–5の場合は1から5の間です。

参照: [`PointRecord`](@ref), [`intensity`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref)
