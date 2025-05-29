```
average_lonlat(var; ignore_nan = true)
```

Return a new `OutputVar` where the values along the longitude and latitude dimensions are averaged arithmetically.

!!! note "Difference from average_lon and average_lat"
    The computation `average_lon(average_lat(var))` computes an average of averages. This function computes the global average over all the values across both the longitude and latitude dimensions. In particular, the results will differ when there are `NaN`s.

