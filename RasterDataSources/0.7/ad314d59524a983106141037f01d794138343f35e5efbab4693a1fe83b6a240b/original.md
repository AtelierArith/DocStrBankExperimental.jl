```
getraster(source::Type{<:ALWB{Union{Deciles,Values},Union{Day,Month,Year}}}, [layer]; date)
```

Download [`ALWB`](@ref) weather data from  [www.bom.gov.au/water/landscape](http://www.bom.gov.au/water/landscape) as values or  deciles with timesteps of `Day`, `Month` or `Year`.

# Arguments

  * `layer`: `Symbol` or `Tuple` of `Symbol` from `(:rain_day, :s0_pct, :ss_pct, :sd_pct, :sm_pct, :qtot, :etot, :e0, :ma_wet, :pen_pet, :fao_pet, :asce_pet, :msl_wet, :dd)`. Without a    `layer` argument, all layers will be downloaded, and a `NamedTuple` of paths returned.

# Keywords

  * `date`: a `DateTime`, `AbstractVector` of `DateTime` or a `Tuple` of start and end dates.   For multiple dates, a `Vector` of multiple filenames will be returned.   ALWB is available with a daily, monthly, and yearly, timestep.

# Example

This will return the file containing annual averages, including your date:

```julia
julia> getraster(ALWB{Values,Year}, :ss_pct; date=Date(2001, 2))
"/your/RASTERDATASOURCES_PATH/ALWB/values/month/ss_pct.nc"
```

Returns the filepath/s of the downloaded or pre-existing files.
