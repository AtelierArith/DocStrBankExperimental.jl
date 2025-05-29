```
scan_angle(p::PointRecord)
scan_angle(points, inds = :)
```

ポイントをスキャンしたレーザービームの角度（度単位）を取得します。この値は、ナディールに対する角度として定義されており（すなわち、飛行機のロールを補正したもの）、0°は真下を指し、負の値は飛行経路の左側、正の値は右側を指します。値の範囲は、PDRF 6–10の場合は−180°から+180°まで0.006°刻み、レガシーPDRF 0–5の場合は−90°から+90°まで1°刻みです。

参照: [`PointRecord`](@ref), [`is_left_to_right`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref)
