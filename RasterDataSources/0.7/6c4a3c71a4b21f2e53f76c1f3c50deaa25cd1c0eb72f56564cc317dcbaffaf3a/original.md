```
getraster(T::Type{CHELSA{Future{Climate}}}, [layer]; date, month) => String
```

Download CHELSA [`Climate`](@ref) data, choosing layers from: `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)`.

See the docs for [`Future`](@ref) for model choices.

Without a layer argument, all layers will be downloaded, and a `NamedTuple` of paths returned.

## Keywords

  * `date`: a `Date` or `DateTime` object, a Vector, or Tuple of start/end dates.   Note that CHELSA CMIP5 only has two datasets, for the periods 2041-2060 and   2061-2080. CMIP6 has datasets for the periods 2011-2040, 2041-2070, and 2071-2100.   Dates must fall within these ranges.
  * `month`: the month of the year, from 1 to 12, or a array or range of months like `1:12`.

## Example

```
using Dates, RasterDataSources
getraster(CHELSA{Future{Climate, CMIP6, GFDLESM4, SSP370}}, :prec; date = Date(2050), month = 1)
```
