```
savi(src::AbstractSatellite; L=0.33)
savi(::Type{AbstractSatellite}, stack::AbstractRasterStack; L=0.33)
savi(nir::AbstractRaster, red::AbstractRaster; L=0.33, scale=1.0, offset=0.0)
```

Compute the Soil Adjusted Vegetation Index (Huete 1988).

SAVI is a vegetation index which attempts to minimize soil brightness influences by introducing a soil-brightness correction factor (L).

SAVI = ((nir - red) / (nir + red + L)) * (1 + L)

# Keywords

  * `L`: The ammount of vegetative cover, where 1.0 means no vegetation and 0.0 means high vegetation.
  * `scale`: The scaling factor to convert digital numbers to reflectance.
  * `offset`: The offset to convert digital numbers to reflectance.
