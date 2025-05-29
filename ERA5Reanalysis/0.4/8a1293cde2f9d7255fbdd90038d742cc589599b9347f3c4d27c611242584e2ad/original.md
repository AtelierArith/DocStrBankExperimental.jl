```
ERA5Region(
    geo :: GeoRegion;
    resolution :: Real = 0,
    ST = String,
    FT = Float64
) -> ereg :: ERA5Region
```

# Argument

  * `geo`  : A `GeoRegion` structure type

# Keyword Argument

  * `resolution` : The spatial resolution that ERA5 reanalysis data will be downloaded/analyzed, and 360 must be a multiple of `resolution`
