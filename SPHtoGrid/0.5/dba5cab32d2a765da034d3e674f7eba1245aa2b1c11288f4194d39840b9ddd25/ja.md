```
surface_brightness_to_luminosity(map::Matrix{<:Real}, par::mappingParameters; unit_factor::Real=1.0)
```

表面輝度のマップをピクセルあたりの光度に変換します。`unit_factor`が指定されている場合は、単位変換を行うためにすべてのピクセルに掛け算されます。
