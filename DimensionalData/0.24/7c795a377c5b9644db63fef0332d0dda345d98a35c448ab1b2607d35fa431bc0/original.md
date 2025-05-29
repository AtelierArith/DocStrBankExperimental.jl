```
units(x) => Union{Nothing,Any}
units(xs:Tuple) => Tuple
unit(A::AbstractDimArray, dims::Tuple) => Tuple
unit(A::AbstractDimArray, dim) => Union{Nothing,Any}
```

Get the units of an array or `Dimension`, or a tuple of of either.

Units do not have a set field, and may or may not be included in `metadata`. This method is to facilitate use in labels and plots when units are available, not a guarantee that they will be. If not available, `nothing` is returned.

Second argument `dims` can be `Dimension`s, `Dimension` types, or `Symbols` for `Dim{Symbol}`.
