```
weighted_average_lonlat(var; ignore_nan = true)
```

緯度と経度の次元に沿って、`cos(lat)` の重みを使って値を算術的に平均した新しい `OutputVar` を返します。

!!! note "average_lon と weighted_average_lat の違い"
    計算 `average_lon(weighted_average_lat(var))` は平均の平均を計算します。この関数は、経度と緯度の両方の次元にわたるすべての値に対して、グローバルな緯度加重平均を計算します。特に、`NaN` がある場合、結果が異なります。

