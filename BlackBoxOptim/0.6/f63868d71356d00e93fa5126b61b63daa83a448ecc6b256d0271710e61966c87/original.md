```
RectSearchSpace(dimranges::AbstractVector; [dimdigits = nothing])
```

Create `RectSearchSpace` with given range of valid values for each dimension and, if specified, `dimdigits` precision for each dimension. Returns `MixedPrecisionRectSearchSpace` if there's at least one dimension with specified precision (dimdigits[i] ≥ 0), otherwise `ContinuousRectSearchSpace`.
