```
is_in_glacier(A::Matrix{F}, distance::I) where {I <: Integer, F <: AbstractFloat}
```

Return a matrix with booleans indicating if a given pixel is at distance at least `distance` in the set of non zero values of the matrix. This usually allows discarding the border pixels of a glacier.

Arguments:

  * `A::Matrix{F}`: Matrix from which to compute the matrix of booleans.
  * `distance::I`: Distance to the border, computed as the number of pixels we need   to move to find a pixel with value zero.
