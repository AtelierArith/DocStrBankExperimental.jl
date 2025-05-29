```
translate(oldPts::AbstractVector{XYPosition}, newPts::AbstractVector{XYPosition})::AffineMap
```

Determines the optimal AffineMap to transform the X-Y coordinates in `oldPts` into the X-Y coordinates in `newPts`. The coordinates in `oldPts` and `newPts` are assumed to represent the same features in the same order and thus must contain the same number of X-Y coordinates.
