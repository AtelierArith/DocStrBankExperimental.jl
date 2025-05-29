```
weighted_average_lat(var::OutputVar; ignore_nan = true)
```

Return a new OutputVar where the values on the latitudes are averaged arithmetically with weights of `cos(lat)`.
