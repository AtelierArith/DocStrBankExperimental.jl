```
aggregate(method, object, scale; kw...)
```

Aggregate a `Raster`, or all arrays in a `RasterStack` or `RasterSeries`, by `scale` using `method`.

# Arguments

  * `method`: a function such as `mean` or `sum` that can combine the value of multiple cells to generate the aggregated cell, or a [`Locus`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.locus) like `Start()` or `Center()` that species where to sample from in the interval.
  * `object`: Object to aggregate, like `AbstractRasterSeries`, `AbstractStack`, `AbstractRaster` or `Dimension`.
  * `scale`: the aggregation factor, which can be an `Int`, a `Tuple` of `Int` for each dimension, or a `:` colon to mean the whole dimension.  You can also use any `Dimension`, `Selector` or `Int` combination you can usually use in `getindex`. `Tuple` of `Pair` or `NamedTuple` where keys are dimension names will also work. Using a `Selector` will determine the scale by the distance from the start  of the index. Selectors will find the first offset and repeat the same aggregation size for the rest.

When the aggregation `scale` of is larger than the array axis, the length of the axis is used.

# Keywords

  * `skipmissing`: if `true`, any `missingval` will be skipped during aggregation, so that   only areas of all missing values will be aggregated to `missingval(dst)`. If `false`,   aggregated areas containing one or more `missingval` will be assigned `missingval`.    `false` by default. `skipmissing` behaviour is independent of function `f`, which is   only applied to completely non-missing values.
  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.
  * `progress`: show a progress bar, `true` by default, `false` to hide.
  * `threaded`: run operations in parallel, `false` by default. In some circumstances `threaded`    can give large speedups over single-threaded operation. This can be true for complicated    geometries written into low-resolution rasters, but may not be for simple geometries with    high-resolution rasters. With very large rasters threading may be counter productive due    to excessive memory use. Caution should also be used: `threaded` should not be used in in-place    functions writing to `BitArray` or other arrays where race conditions can occur.
  * `vebose`: whether to print messages about potential problems. `true` by default.

# Example

```jldoctest
using Rasters, RasterDataSources, Statistics, Plots
import ArchGDAL
using Rasters: Center
st = RasterStack(WorldClim{Climate}; month=1)
ag = aggregate(Center(), st, (Y(20), X(20)); skipmissingval=true, progress=false)
plot(ag)
savefig("build/aggregate_example.png"); nothing
# output

```

![aggregate](aggregate_example.png)

Note: currently it is faster to aggregate over memory-backed arrays. Use [`read`](@ref) on `src` before use where required.
