```
gradient(coord::AbstractVector{C}, arr::AbstractVector{A}; method::Symbol=:second_order) where {C<:Real, A<:Real}
```

The finite difference gradient. The returned gradient has the same shape as the input array.

`method` of the gradient can be one of [:backward, :central, :forward, :second*order, :third*order]

For `:central` the gradient is computed using second order accurate central differences in the interior points and first order accurate one-sides (forward or backward) differences at the boundaries.

For `:second_order` the gradient is computed using second order accurate central differences in the interior points, and 2nd order differences at the boundaries.

For `:third_order` the gradient is computed from the cubic spline passing through the points
