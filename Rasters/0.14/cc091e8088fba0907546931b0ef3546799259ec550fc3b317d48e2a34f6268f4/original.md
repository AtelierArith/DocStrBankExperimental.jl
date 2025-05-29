```
trim(x; dims::Tuple, pad::Int)
```

Trim `missingval(x)` from `x` for axes in `dims`, returning a view of `x`.

# Arguments

  * `x`: A `Raster` or `RasterStack`. For stacks, all layers must having   missing values for a pixel for it to be trimmed.

# Keywords

  * `dims`: By default `dims=(XDim, YDim)`, so that trimming keeps the area    of `X` and `Y` that contains non-missing values along all other dimensions.
  * `pad`: The trimmed size will be padded by `pad` on all sides, although   padding will not be added beyond the original extent of the array.

As `trim` is lazy, `filename` and `suffix` keywords are not used.

# Example

Create trimmed layers of Australian habitat heterogeneity.

```jldoctest
using Rasters, RasterDataSources, Plots
layers = (:evenness, :range, :contrast, :correlation)
st = RasterStack(EarthEnv{HabitatHeterogeneity}, layers)

# Roughly cut out australia
ausbounds = X(100 .. 160), Y(-50 .. -10)
aus = st[ausbounds...]
a = plot(aus)

# Trim missing values and plot
b = plot(trim(aus))

savefig(a, "build/trim_example_before.png");
savefig(b, "build/trim_example_after.png"); nothing

# output

```

### Before `trim`:

![before trim](trim_example_before.png)

### After `trim`:

![after trim](trim_example_after.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
