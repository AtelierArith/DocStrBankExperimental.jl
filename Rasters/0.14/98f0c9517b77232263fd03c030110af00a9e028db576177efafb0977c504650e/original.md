```
classify(x, pairs; lower=(>=), upper=(<), others=nothing)
classify(x, pairs...; lower, upper, others)
```

Create a new array with values in `x` classified by the values in `pairs`.

`pairs` can hold tuples fo values `(2, 3)`, a `Fix2` function e.g. `<=(1)`, a `Tuple` of `Fix2` e.g. `(>=(4), <(7))`, or an IntervalSets.jl interval, e.g. `3..9` or `OpenInterval(10, 12)`. `pairs` can also be a `n * 3` matrix where each row is lower bounds, upper bounds, replacement.

If tuples or a `Matrix` are used, the `lower` and `upper` keywords define how the lower and upper boundaries are chosen.

If `others` is set other values not covered in `pairs` will be set to that values.

# Arguments

  * `x`: a `Raster` or `RasterStack`
  * `pairs`: each pair contains a value and a replacement, a tuple of lower and upper   range and a replacement, or a Tuple of `Fix2` like `(>(x), <(y)`.

# Keywords

  * `lower`: Which comparison (`<` or `<=`) to use for lower values, if `Fix2` are not used.
  * `upper`: Which comparison (`>` or `>=`) to use for upper values, if `Fix2` are not used.
  * `others`: A value to assign to all values not included in `pairs`.   Passing `nothing` (the default) will leave them unchanged.

# Example

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots
A = Raster(WorldClim{Climate}, :tavg; month=1)
classes = <=(15) => 10,
          15..25 => 20,
          25..35 => 30,
          >(35) => 40
classified = classify(A, classes; others=0, missingval=0)
plot(classified; c=:magma)

savefig("build/classify_example.png"); nothing

# output
```

![classify](classify_example.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
