```
surface_brightness_to_luminosity(map::Matrix{<:Real}, pixelSideLength::Real; unit_factor::Real=1.0)
```

表面輝度のマップをピクセルあたりの光度に変換します。`pixelSideLength`をピクセルの直径として使用します（単位は`[kpc]`）。`unit_factor`が提供されると、単位変換を行うためにすべてのピクセルに掛け算されます。
