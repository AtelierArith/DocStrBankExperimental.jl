```
curvature(radec::AbstractVector{RadecMPC{T}}) where {T <: Real}
```

Return:

  * A vector with the geodesic curvature and along track acceleration of `radec`.
  * The curvature covariance matrix.

!!! reference
    See section 5.1 of https://doi.org/10.1016/j.icarus.2007.11.033

