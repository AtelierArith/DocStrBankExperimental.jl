```
DimIndices <: AbstractArray

DimIndices(x)
DimIndices(dims::Tuple)
DimIndices(dims::Dimension)
```

Like `CartesianIndices`, but for `Dimension`s. Behaves as an `Array` of `Tuple` of `Dimension(i)` for all combinations of the axis indices of `dims`.

This can be used to view/index into arbitrary dimensions over an array, and is especially useful when combined with `otherdims`, to iterate over the indices of unknown dimension.
