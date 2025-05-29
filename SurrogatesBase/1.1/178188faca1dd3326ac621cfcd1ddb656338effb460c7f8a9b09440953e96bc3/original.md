```
update!(s, new_xs::AbstractVector, new_ys::AbstractVector)
```

Include data `new_ys` at points `new_xs` into the surrogate `s`, i.e., refit the surrogate `s` to incorporate new data points.

If the surrogate `s` is a deterministic surrogate, the `new_ys` correspond to function evaluations, if `s` is a stochastic surrogate, the `new_ys` are samples from a conditional probability distribution.

Use `update!(s, eachslice(X, dims = 2), new_ys)` if `X` is a matrix.
