```
ALWB{Union{Deciles,Values},Union{Day,Month,Year}} <: RasterDataSource
```

Data from the Australian Landscape Water Balance (ALWB) data source.

See: [www.bom.gov.au/water/landscape](http://www.bom.gov.au/water/landscape)

The dataset contains NetCDF files. They have a time dimension so that multiple dates are stored in each file. 

The available layers are: `(:rain_day, :s0_pct, :ss_pct, :sd_pct, :sm_pct, :qtot, :etot, :e0, :ma_wet, :pen_pet, :fao_pet, :asce_pet, :msl_wet, :dd)`, available in daily, monthly and  annual resolutions, and as `Values` or relative `Deciles`.

`getraster` for `ALWB` must use a `date` keyword to specify the date to download.

See the [`getraster`](@ref) docs for implementation details.
