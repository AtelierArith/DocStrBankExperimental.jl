```
average_lat(var::OutputVar; ignore_nan = true, weighted = false)
```

Return a new OutputVar where the values on the latitudes are averaged arithmetically.

When `weighted` is `true`, weight the average over `cos(lat)`.
