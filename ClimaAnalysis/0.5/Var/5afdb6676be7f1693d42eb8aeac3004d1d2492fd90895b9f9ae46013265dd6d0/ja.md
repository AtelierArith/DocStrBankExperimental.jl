```
average_lat(var::OutputVar; ignore_nan = true, weighted = false)
```

緯度の値が算術的に平均される新しい OutputVar を返します。

`weighted` が `true` の場合、平均を `cos(lat)` で重み付けします。
