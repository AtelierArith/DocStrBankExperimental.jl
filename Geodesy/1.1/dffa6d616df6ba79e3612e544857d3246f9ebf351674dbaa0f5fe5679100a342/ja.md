```
euclidean_distance(utm1, utm2, zone, isnorth, [datum = wgs84])
euclidean_distance(a, utm2, zone, isnorth, [datum = wgs84])
euclidean_distance(utm1, b, zone, isnorth, [datum = wgs84])
```

もし1つまたは両方の点がUTMの場合、ユークリッド距離を決定するためにゾーン（特に半球、isnorth = true/false）が必要です。
