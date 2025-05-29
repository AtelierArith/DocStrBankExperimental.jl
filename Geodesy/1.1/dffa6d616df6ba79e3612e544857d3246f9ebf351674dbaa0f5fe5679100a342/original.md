```
euclidean_distance(utm1, utm2, zone, isnorth, [datum = wgs84])
euclidean_distance(a, utm2, zone, isnorth, [datum = wgs84])
euclidean_distance(utm1, b, zone, isnorth, [datum = wgs84])
```

If one or both points are UTM, we need the zone (and particularly the hemisphere, isnorth = true/false) to determine the Euclidean distance.
