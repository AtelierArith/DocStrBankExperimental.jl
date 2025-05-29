```
lon, lat = randgeo(n; rad=false, limits=nothing, do360=false)
```

Generate random longitude and latitude coordinates.

By default the coordinates are in degrees and in the [-180 180] range. Set `do360` to `true` to get the coordinates in the [0 360] range. Set `rad` to `true` to get the coordinates in radians instead of degrees.

Optionally, you can pass a 4-element array or tuple with the limits of the coordinates. `limits` must then contain the lon*min, lon*max, lat*min, lat*max of the region where you want to generate random points.
