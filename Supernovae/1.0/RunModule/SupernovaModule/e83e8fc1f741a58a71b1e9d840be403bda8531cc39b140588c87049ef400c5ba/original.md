```
Supernova(data::Dict{String,Any}, config::Dict{String,Any})
```

Load in a supernova from `data`, which has a number of keys containing supernova data and options.

  * `NAME::String`: Name of the supernova
  * `ZEROPOINT::Float64`: Supernova zeropoint
  * `ZEROPOINT_UNIT::String`: Unitful unit of zeropoint, default to AB_mag
  * `REDSHIFT::Float64`: Supernova redshift
  * `MAX_FLUX_ERR::Float64`: Maximum allowed flux error, default to inf
  * `MAX_FLUX_ERR_UNIT::String`: Unitful unit of maximum flux error
  * `PEAK_TIME::Union{Bool, Float64}`: If bool, whether to set time relative to peak flux, if Float64, set time relative to PEAK_TIME
  * `OBSERVATIONS::Vector{Dict{String,Any}}`: Data to be turned into a [`Lightcurve`](@ref)
