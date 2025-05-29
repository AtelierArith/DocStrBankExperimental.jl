```julia
curl(
    u::SpeedyWeather.RingGrids.AbstractGridArray,
    v::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

グリッド上の2つのベクトル成分 `u, v` のカール (∇×)。1/coslat スケーリングを適用し、スペクトル空間に変換してスペクトルカールを返します。単位球体上で作用し、`radius` キーワード引数が提供されない限り、1/radius スケーリングを省略します。
