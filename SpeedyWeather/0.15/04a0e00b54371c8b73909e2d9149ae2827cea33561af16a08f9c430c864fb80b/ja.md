```julia
coriolis(
    grid::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

`grid`のようなグリッド上で、`rotation` [1/s]の惑星のコリオリパラメータ`f`を返します。デフォルトは地球の回転です。
