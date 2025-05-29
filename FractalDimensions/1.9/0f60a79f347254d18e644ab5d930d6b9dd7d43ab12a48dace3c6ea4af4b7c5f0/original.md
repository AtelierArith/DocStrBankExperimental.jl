```
linear_regions(x, y; dxi, tol) → lrs, tangents
```

Apply the algorithm described by [`LargestLinearRegion`](@ref), and return the indices of `x` that correspond to the linear regions, `lrs`, and the `tangents` at each region (obtained via a second linear regression at each accumulated region). `lrs` is hence a vector of `UnitRange`s.
