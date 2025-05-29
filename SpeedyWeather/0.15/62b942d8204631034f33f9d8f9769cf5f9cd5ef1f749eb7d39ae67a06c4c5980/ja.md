```julia
coriolis(
    grid::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

グリッド `Grid` のコリオリパラメータ `f` を、回転数 `rotation` [1/s] の惑星上で解像度 `nlat_half` で返します。デフォルトは地球の回転です。
