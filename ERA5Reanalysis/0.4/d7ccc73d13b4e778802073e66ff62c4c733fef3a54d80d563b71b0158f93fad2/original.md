```
ERA5Region(
    ID :: AbstractString;
    resolution :: Real = 0,
    ST = String,
    FT = Float64
) -> ereg :: ERA5Region
```

# Argument

  * `ID` : The ID used to specify the `GeoRegion`

# Keyword Argument

  * `resolution` : The spatial resolution that ERA5 reanalysis data will be downloaded/analyzed, and 360 must be a multiple of `resolution`
