```
vsubset = CommonDataModel.@select(v,expression)
dssubset = CommonDataModel.@select(ds,expression)
```

Return a subset of the variable `v` (or dataset `ds`) satisfying the condition `expression` as a view. The condition has the following form:

`condition₁ && condition₂ && condition₃ ... conditionₙ`

Every condition should involve a single 1D variable (typically a coordinate variable, referred as `coord` below). If `v` is a variable, the related 1D variable should have a shared dimension with the variable `v`. All local variables need to have a `$` prefix (see examples below). This macro is experimental and subjected to change.

Every condition can either perform:

  * a nearest match: `coord ≈ target_coord` (for `≈` type `\approx` followed by the TAB-key). Only the data corresponding to the index closest to `target_coord` is loaded.
  * a nearest match with tolerance: `coord ≈ target_coord ± tolerance`. As before, but if the difference between the closest value in `coord` and `target_coord` is larger (in absolute value) than `tolerance`, an empty array is returned.
  * a condition operating on scalar values. For example, a `condition` equal to `10 <= lon <= 20` loads all data with the longitude between 10 and 20 or `abs(lat) > 60` loads all variables with a latitude north of 60° N and south of 60° S (assuming that the has the 1D variables `lon` and `lat` for longitude and latitude).

Only the data which satisfies all conditions is loaded. All conditions must be chained with an `&&` (logical and). They should not contain additional parenthesis or other logical operators such as `||` (logical or).

To convert the view into a regular array one can use `collect`, `Array` or regular indexing. As in julia, views of scalars are wrapped into a zero dimensional arrays which can be dereferenced by using `[]`. Modifying a view will modify the underlying file (if the file is opened as writable, otherwise an error is issued).

As for any view, one can use `parentindices(vsubset)` to get the indices matching a select query.

## Examples

Create a sample file with random data:

```julia
using NCDatasets, Dates
using CommonDataModel: @select
# or
# using NCDatasets: @select

fname = "sample_file.nc"
lon = -180:180
lat = -90:90
time = DateTime(2000,1,1):Day(1):DateTime(2000,1,3)
SST = randn(length(lon),length(lat),length(time))

ds = NCDataset(fname,"c")
defVar(ds,"lon",lon,("lon",));
defVar(ds,"lat",lat,("lat",));
defVar(ds,"time",time,("time",));
defVar(ds,"SST",SST,("lon","lat","time"));


# load by bounding box
v = @select(ds["SST"],30 <= lon <= 60 && 40 <= lat <= 80)

# substitute a local variable in condition using $
lonr = (30,60) # longitude range
latr = (40,80) # latitude range

v = @select(ds["SST"],$lonr[1] <= lon <= $lonr[2] && $latr[1] <= lat <= $latr[2])

# You can also select based on `ClosedInterval`s from `IntervalSets.jl`.
# Both 30..60 and 60 ± 20 construct `ClosedInterval`s, see their documentation for details.

lon_interval = 30..60
lat_interval = 60 ± 20
v = @select(ds["SST"], lon ∈ $lon_interval && lat ∈ $lat_interval)

# get the indices matching the select query
(lon_indices,lat_indices,time_indices) = parentindices(v)

# get longitude matchting the select query
v_lon = v["lon"]

# find the nearest time instance
v = @select(ds["SST"],time ≈ DateTime(2000,1,4))

# find the nearest time instance but not earlier or later than 2 hours
# an empty array is returned if no time instance is present

v = @select(ds["SST"],time ≈ DateTime(2000,1,3,1) ± Hour(2))

close(ds)
```

Any 1D variable with the same dimension name can be used in `@select`. For example, if we have a time series of temperature and salinity, the temperature values can also be selected based on salinity:

```julia
using NCDatasets, Dates
using CommonDataModel: @select
fname = "sample_series.nc"
# create a sample time series
time = DateTime(2000,1,1):Day(1):DateTime(2009,12,31)
salinity = randn(length(time)) .+ 35
temperature = randn(length(time))

NCDataset(fname,"c") do ds
    defVar(ds,"time",time,("time",));
    defVar(ds,"salinity",salinity,("time",));
    defVar(ds,"temperature",temperature,("time",));
end

ds = NCDataset(fname)

# load all temperature data from January where the salinity is larger than 35.
v = @select(ds["temperature"],Dates.month(time) == 1 && salinity >= 35)

# this is equivalent to:
v2 = ds["temperature"][findall(Dates.month.(time) .== 1 .&& salinity .>= 35)]

v == v2
# returns true
close(ds)
```

!!! note
    For optimal performance, one should try to load contiguous data ranges, in particular when the data is loaded over HTTP/OPeNDAP.

