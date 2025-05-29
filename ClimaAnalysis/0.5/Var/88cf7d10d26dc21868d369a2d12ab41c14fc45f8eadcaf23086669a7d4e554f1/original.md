```
weighted_average_lonlat(var; ignore_nan = true)
```

Return a new `OutputVar` where the values along the longitude and latitude dimensions are averaged arithmetically with weights of `cos(lat)` along the latitude dimension.

!!! note "Difference from average_lon and weighted_average_lat"
    The computation `average_lon(weighted_average_lat(var))` computes an average of averages. This function computes the global latitude-weighted average over all the values across both the longitude and latitude dimensions. In particular, the results differ when there are `NaN`s.

