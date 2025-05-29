```
gps_time(p::PointRecord)
gps_time(points, inds = :)
```

PDRF 1および3〜10でポイントが記録されたGPS時間を取得します。GPS時間が含まれていないPDRFの場合は`missing`を返します。時間値の解釈については[`LAS`](@ref)の`has_adjusted_gps_time`フィールドを参照してください。

関連情報: [`PointRecord`](@ref)
