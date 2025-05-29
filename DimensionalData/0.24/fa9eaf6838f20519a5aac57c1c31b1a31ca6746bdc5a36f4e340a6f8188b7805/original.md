```
DimKeys <: AbstractArray

DimKeys(x)
DimKeys(dims::Tuple)
DimKeys(dims::Dimension)
```

Like `CartesianIndices`, but for the lookup values of Dimensions. Behaves as an `Array` of `Tuple` of `Dimension(At(lookupvalue))` for all combinations of the lookup values of `dims`.
