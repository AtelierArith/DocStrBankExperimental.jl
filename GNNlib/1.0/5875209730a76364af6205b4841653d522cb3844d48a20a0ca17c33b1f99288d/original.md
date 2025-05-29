```
w_mul_xj(xi, xj, w) = reshape(w, (...)) .* xj
```

Similar to [`e_mul_xj`](@ref) but specialized on scalar edge features (weights).
