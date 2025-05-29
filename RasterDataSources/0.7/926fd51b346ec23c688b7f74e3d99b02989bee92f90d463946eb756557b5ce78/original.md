```
getraster(T::Type{CHELSA{Future{BioClim}}}, [layer]; date) => String
```

Download CHELSA [`BioClim`](@ref) data, choosing layers from: `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)`.

See the docs for [`Future`](@ref) for model choices.

Without a layer argument, all layers will be downloaded, and a `NamedTuple` of paths  returned.

## Keywords

  * `date`: a `Date` or `DateTime` object, a Vector, or Tuple of start/end dates.   Note that CHELSA CMIP5 only has two datasets, for the periods 2041-2060 and   2061-2080. CMIP6 has datasets for the periods 2011-2040, 2041-2070, and 2071-2100.   Dates must fall within these ranges.

## Example

```julia
using RasterDataSources, Dates
getraster(CHELSA{Future{BioClim, CMIP6, GFDLESM4, SSP370}}, 1, date = Date(2050))
```
