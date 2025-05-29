```
function crop(ga::GeoArray, cbox::NamedTuple{(:min_x, :min_y, :max_x, :max_y),Tuple{Float64,Float64,Float64,Float64}})
```

Crop input GeoArray by coordinates (box or another GeoArray). If the coordinates range is larger than the GeoArray, only the overlapping part is given in the result.
