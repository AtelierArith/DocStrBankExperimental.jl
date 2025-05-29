```
getraster(T::Union{Type{<:ModisProduct}, Type{MODIS{X}}}, [layer::Union{Tuple,AbstractVector,Integer, Symbol}]; kwargs...) => Union{String, AbstractVector, NamedTuple}
```

Download [`MODIS`](@ref) data for a given [`ModisProduct`](@ref) as ASCII raster(s).

# Arguments

  * `layer`: `Integer` or tuple/range of `Integer` or `Symbol`s. Without a `layer` argument, all layers will be downloaded, and a `NamedTuple` of paths returned.

Available layers for a given product can be looked up using [`RasterDataSources.layerkeys(T::Type{<:ModisProduct})`](@ref).

# Keywords

  * `lat` and `lon`: Coordinates in decimal degrees of the approximate center of the raster. The MODIS API will try to match its pixel grid system as close as possible to those coordinates.
  * `km_ab` and `km_lr`: Half-width and half-height of the raster in kilometers (kilometers above/below and left/right). Currently only `Integer` values are supported, up to 100.
  * `date`: `String`, `Date`, `DateTime`, `AbstractVector` of dates or `Tuple` of a start and end date for the request. `String`s should be in format YYYY-MM-DD but can be in similar formats as long as they are comprehensible by `Dates.Date`. The available date interval for MODIS is 16 days, reset every first of January.

# Example

Download 250m NDVI in the western part of Britanny, France, from winter to late spring, 2002:

```julia
julia> getraster(MOD13Q1, :NDVI; lat = 48.25, lon = -4, km_ab = 50, km_lr = 50, date = (Date(2002,1,1), Date(2002,6,1)))

    10-element Vector{String}:
    "/your/path/MODIS/MOD13Q1/250m_16_days_NDVI/47.8313_-4.5899_2002-01-01.asc"
    ...
    "/your/path/MODIS/MOD13Q1/250m_16_days_NDVI/47.8313_-4.5899_2002-05-25.asc"
```

Will attempt to download several files, one for each date and layer combination, and returns the filepath/s of the downloaded or pre-existing files. Coordinates in the file names correspond to the lower-left corner of the raster.
