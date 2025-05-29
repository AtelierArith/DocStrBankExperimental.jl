```
t′(r̄::AbstractCoordinate, t:Time, r̄′::Coordinate, c::Quantity)
```

観測点（`r̄`,`t`）での媒質の光速 `c` を通じて、源点 `r̄′` での遅延時間を計算します。

# 引数

  * `r̄::UnitfulCoordinateSystems.AbstractCoordinate`: 観測点の空間位置
  * `t::Unitful.Time`: 観測点での時間
  * `r̄′::UnitfulCoordinateSystems.AbstractCoordinate`: 源点の空間位置
  * `c::Quantity`: r̄′ と r̄ の間の媒質における単位付き光速
