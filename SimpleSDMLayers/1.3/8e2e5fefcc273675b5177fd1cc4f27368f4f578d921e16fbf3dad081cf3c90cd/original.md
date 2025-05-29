```
cellarea(layer::T; R = 6371.0)
```

Returns the area of each cell in km², assuming a radius of the Earth or `R` (in km). This is only returned for layers in WGS84, which can be forced with `interpolate`.
