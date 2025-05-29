```
classify!(x, pairs...; lower, upper, others)
classify!(x, pairs; lower, upper, others)
```

Classify the values of `x` in-place, by the values in `pairs`.

If `Fix2` is not used, the `lower` and `upper` keywords

If `others` is set other values not covered in `pairs` will be set to that values.

# Arguments

  * `x`: a `Raster` or `RasterStack`
  * `pairs`: each pair contains a value and a replacement, a tuple of lower and upper   range and a replacement, or a Tuple of `Fix2` like `(>(x), <(y)`.

# Keywords

  * `lower`: Which comparison (`<` or `<=`) to use for lower values, if `Fix2` are not used.
  * `upper`: Which comparison (`>` or `>=`) to use for upper values, if `Fix2` are not used.
  * `others`: A value to assign to all values not included in `pairs`.   Passing `nothing` (the default) will leave them unchanged.

# Example

`classify!` to disk, with key steps:

  * copying a tempory file so we don't write over the RasterDataSources.jl version.
  * use `open` with `write=true` to open the file with disk-write permissions.
  * use `Float32` like `10.0f0` for all our replacement values and `other`, because   the file is stored as `Float32`. Attempting to write some other type will fail.

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots
# Download and copy the file
filename = getraster(WorldClim{Climate}, :tavg; month=6)
tempfile = tempname() * ".tif"
cp(filename, tempfile)
# Define classes
classes = (5, 15) => 10,
          (15, 25) => 20,
          (25, 35) => 30,
          >=(35) => 40
# Open the file with write permission
open(Raster(tempfile); write=true) do A
    classify!(A, classes; others=0)
end
# Open it again to plot the changes
plot(Raster(tempfile); c=:magma)

savefig("build/classify_bang_example.png"); nothing

# output
```

![classify!](classify_bang_example.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
