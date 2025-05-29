```
average_lonlat(var; ignore_nan = true)
```

経度と緯度の次元に沿って値を算術的に平均した新しい `OutputVar` を返します。

!!! note "average_lon と average_lat の違い"
    計算 `average_lon(average_lat(var))` は平均の平均を計算します。この関数は、経度と緯度の両方の次元にわたるすべての値のグローバル平均を計算します。特に、`NaN` がある場合、結果は異なります。

