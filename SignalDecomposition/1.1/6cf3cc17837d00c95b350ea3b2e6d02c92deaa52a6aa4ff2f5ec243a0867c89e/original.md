```
ProductInversion(r, μ; verbose=false) <: Decomposition
```

Decompose a timeseries `s` into a **product** `x * r`, given that you have a good estimate of the second factor `r` (the "input") and you need `x` (the "multiplier") but you can't do simply `x =  s ./ r` because `r` contains zeros.

This method works well when the characteristic timescales of `x` are comparable, or larger than those of `r` but not much smaller.

The second argument `μ` is a regularization parameter. In short, we estimate `r` by minimizing a cost with two components: that `x` is close to `s/r` and that `x` is smooth. `μ` is the multiplier of the smoothness cost.

You can give a vector as `μ`. The process will be repeated for all `μ` and the [`rmse`](@ref) between `s` and the estimated `x * r` will be computed. The `x` that gives the least error will be returned finally. If `verbose = true`, the method also prints the pairs `(μ, err)` for each `μ`.

Use the low level `SignalDecomposition.matrix_invert(s, r, μ::Real) → x, err` to get the error values.
