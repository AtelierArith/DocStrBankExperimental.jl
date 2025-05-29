```
icp(pts1::AbstractVector{T}, pts2::AbstractVector{T}; maxiter=10, tol=0.9)
```

Implements the iterative closest point algorithm.  Transforms `pts2` through rotations and  translations to come as close as possible to `pts1` using a least-squares metric.

The intention is that `pts1` is the super-set of points in `pts2`.  When aligned most of the points in `pts2` will match up with points in `pts1`.
