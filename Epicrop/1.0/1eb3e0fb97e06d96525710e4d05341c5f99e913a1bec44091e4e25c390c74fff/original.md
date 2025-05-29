```
sheathblight(wth::DataFrames.AbstractDataFrame, emergence::Dates.Date)
```

Run a healthy-latent-infectious-postinfectious (HLIP) model using weather data and optimal curve values for rice sheath blight caused by *Rhizoctonia solani* AG1-1A Kühn.

## Arguments

  * `wth::DataFrames.AbstractDataFrame`: weather data on a daily time-step containing data with the following values.

      * `YYYYMMDD::Union{AbstractString, Dates.Date}: the date in ISO8601 format, *i.e.*, YYYY-MM-DD
      * `DOY::Int64`: the consecutive day of year, commonly called "Julian date"
      * `TEMP::AbstractFloat`: the mean daily temperature (°C)
      * `RHUM::AbstractFloat`: the mean daily relative humidity (%)
      * `RAIN::AbstractFloat`: the mean daily rainfall (mm)
  * `emergence::Union{AbstractString, Dates.Date}`: the expected date of plant emergence. From Table 1 Savary *et al.* 2012.
  * `duration::Int64`: the simulation duration (growing season length in days), defaults to 120 as in Savary *et al.* 2012. From Table 1 Savary *et al.* 2012.

## Returns

A `DataFrames.DataFrame` with predictions for sheath blight severity. Latitude and longitude are included for mapping purposes if they are present in the input weather data. See [`hlipmodel`](@ref) for a full description of the return values.

## Notes

This is one of a family of helper functions. Also see [`bacterialblight`](@ref), [`brownspot`](@ref), [`leafblast`](@ref) and [`tungro`](@ref).

## Examples

```julia
julia> using Epicrop

julia> using DelimitedFiles

julia> using DataFrames

julia> data, header = readdlm(joinpath(
                                dirname(pathof(Epicrop)),
                                    "..", "docs", "src", "assets",
                                        "POWER_data_LB_PHI_2000_ws.csv"),
                                ',', header=true)

julia> w = DataFrame(data, vec(header))

julia> emergence = "2000-07-01"

julia> sheathblight(w, emergence)
```
