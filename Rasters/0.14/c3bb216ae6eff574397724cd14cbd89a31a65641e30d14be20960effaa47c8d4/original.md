```
mosaic(f, regions...; kw...)
mosaic(f, regions; kw...)
```

Combine `regions` of `Raster` or `RasterStack` into a single object,  using the function `f` to combine overlapping areas.

# Arguments

  * `f`: A reducing function for values where `regions` overlap.    Note that common base functions    (`mean`, `sum`, `prod`, `first`, `last`, `minimum`, `maximum`,  `length`)   are optimised and will work on many memory or disk based files,   but user-defined functions may fail at larger scales unless `op` is passes as a keyword.
  * `regions`: Iterable of `Raster` or `RasterStack`. Using an `AbstractArray` is    usually better than a `Tuple` or splat when there are many regions.

# Keywords

  * `missingval`: Fills empty areas, and defaults to the   `missingval` of the first region.
  * `op`: an operator for the reduction, e.g. `add_sum` for `sum`.    For common methods like `sum` these are known and detected for you,    but you can provide it manually for other functions, so they continue   to work at large scales.
  * `atol`: Absolute tolerance for comparison between index values.   This is often required due to minor differences in range values   due to floating point error. It is not applied to non-float dimensions.   A tuple of tolerances may be passed, matching the dimension order.
  * `progress`: show a progress bar, `true` by default, `false` to hide.
  * `read`: `read` lazy raster regions before writing them. This may help   if there are chunk alignment issues between the source and dest rasters.   `false` by default.
  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.
  * `force`: `false` by default. If `true` it force writing to a file destructively, even if it already exists.

If your mosaic has has apparent line errors, increase the `atol` value.

# Example

Here we cut out Australia and Africa from a stack, and join them with `mosaic`.

```jldoctest
using Rasters, RasterDataSources, NaturalEarth, DataFrames, Dates, Plots
import ArchGDAL

countries = naturalearth("admin_0_countries", 110) |> DataFrame
climate = RasterStack(WorldClim{Climate}, (:tmin, :tmax, :prec, :wind); month=July)
country_climates = map(("Norway", "Denmark", "Sweden")) do name
    country = subset(countries, :NAME => ByRow(==(name)))
    trim(mask(climate; with=country); pad=10)
end
scandinavia_climate = trim(mosaic(first, country_climates; progress=false))
plot(scandinavia_climate)
savefig("build/mosaic_example_combined.png"); nothing

# output

```

### Mosaic of countries

![mosaic](mosaic_example_combined.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
