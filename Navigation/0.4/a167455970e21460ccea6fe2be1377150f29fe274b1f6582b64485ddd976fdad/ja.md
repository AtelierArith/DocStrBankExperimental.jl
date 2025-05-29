```
destination_point(start_pos::Point, distance::Float64, bearing::Float64[,
 radius::Float64=Rₑ_m])
```

与えられた `start_pos` [deg]、初期 `bearing` (北から時計回り) [deg]、`distance` [m]、および地球の `radius` [m] に基づいて、(最短距離) 大円弧に沿って `destina­tion_point` [deg] を計算します。 (距離は地球の半径と同じ半径を使用する必要があります。)

出典: www.movable-type.co.uk/scripts/latlong.html
