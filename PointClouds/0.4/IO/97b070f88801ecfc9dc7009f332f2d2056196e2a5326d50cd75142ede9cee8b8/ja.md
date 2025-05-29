```
scan_angle(Integer, p::PointRecord)
scan_angle(Integer, points, inds = :)
```

ポイントレコードの「生」のスキャン角度を、PDRFに応じて符号付き8ビットまたは16ビット整数として取得します。値は、PDRF 6～10の場合は0.006°の増分、レガシーPDRF 0～5の場合は1°の増分に対応します。

参照: [`PointRecord`](@ref), [`is_left_to_right`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref)
