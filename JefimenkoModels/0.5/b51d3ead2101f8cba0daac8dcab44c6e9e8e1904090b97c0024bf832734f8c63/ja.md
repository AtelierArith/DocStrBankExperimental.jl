```
t′(r̄::Coordinate, t:Time, r̄′::Coordinate, media::PropagationMedia)
```

観測点（`r̄`,`t`）におけるソース点 `r̄′` での遅延時間を、`伝播媒体` を通じて計算します。

# 引数

  * `r̄::UnitfulCoordinateSystems.Coordinate`: 観測点の空間位置
  * `t::Unitful.Time`: 観測点での時間
  * `r̄′::UnitfulCoordinateSystems.Coordinate`: ソース点の空間位置
  * `media::PropagationMedia`: `r̄′` と `r̄` の間の媒体の特性
