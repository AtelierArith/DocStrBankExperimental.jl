```
extend(xs...; [to])
extend(xs; [to])
extend(x::Union{AbstractRaster,AbstractRasterStack}; to, kw...)
```

Extend one or multiple [`AbstractRaster`](@ref) to match the area covered by all `xs`, or by the keyword argument `to`.

# Keywords

  * `to`: the Raster or dims to extend to. If no `to` keyword is passed, the largest   shared area of all `xs` is used.
  * `touches`: `true` or `false`. Whether to use `Touches` wrapper on the object extent.  When lines need to be included in e.g. zonal statistics, `true` shoudle be used.
  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.

```jldoctest
using Rasters, RasterDataSources, Plots
evenness = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)
rnge = Raster(EarthEnv{HabitatHeterogeneity}, :range)

# Roughly cut out South America
sa_bounds = X(-88 .. -32), Y(-57 .. 13)
sa_evenness = evenness[sa_bounds...]

# Extend range to match the whole-world raster
sa_range = extend(sa_evenness; to=rnge)
plot(sa_range)

savefig("build/extend_example.png");
nothing
# output
```

![extend](extend_example.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
