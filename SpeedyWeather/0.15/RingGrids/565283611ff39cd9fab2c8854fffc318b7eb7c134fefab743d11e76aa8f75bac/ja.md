```julia
eachring(
    grid1::SpeedyWeather.RingGrids.AbstractGridArray,
    grids::SpeedyWeather.RingGrids.AbstractGridArray...
) -> Any

```

`eachring(grid)`と同様ですが、`grids_match`に従ってすべての`grids`が（非パラメトリックグリッドタイプ、nlat_halfおよび長さ）であることを評価するために境界チェックを実行します。
