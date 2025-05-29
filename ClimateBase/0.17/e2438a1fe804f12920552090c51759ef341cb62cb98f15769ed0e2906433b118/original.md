```
ClimArray(A::Array, dims::Tuple; name = "", attrib = nothing)
```

`ClimArray` is a structure that contains numerical array data bundled with dimensional information, a name and an `attrib` field (typically a dictionary) that holds general attributes. You can think of `ClimArray` as a in-memory representation of a CFVariable.

At the moment, a `ClimArray` is using `DimArray` from DimensionalData.jl, and all basic handling of `ClimArray` is offered by `DimensionalData` (see below).

`ClimArray` is created by passing in standard array data `A` and a tuple of dimensions `dims`. See [`ncread`](@ref) to automatically create a `ClimArray` from a .nc file. For obtaining the raw numeric values of a `ClimArray` or any of its dimensions, use the function [`gnv`](@ref).

## Example

```julia
using ClimateBase, Dates
Time = ClimateBase.Ti # more intuitive name for time dimension
lats = -90:5:90
lons = 0:10:359
t = Date(2000, 3, 15):Month(1):Date(2020, 3, 15)
# dimensional information:
dimensions = (Lon(lons), Lat(lats), Time(t))
data = rand(36, 37, 241) # numeric data
A = ClimArray(data, dimensions)
```
