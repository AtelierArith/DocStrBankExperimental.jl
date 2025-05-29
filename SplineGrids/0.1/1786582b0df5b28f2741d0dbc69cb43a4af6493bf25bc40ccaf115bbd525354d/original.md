```
evaluate!(spline_dimension)
```

Per sample point, get the value of the `spline_dimension.degree + 1` basis functions that have a non-zero value for that sample point. This is based on the Cox-de Boor recursion formula.

The l-th sample point `t` has sample index `i`, meaning that `t ∈ [tᵢ, tᵢ₊₁)`. Therefore `Bᵢ₀(t) = 1, Bⱼ₀(t) = 0 for j ≠ i`. For degree `k`, `t` is in the domain of `Bⱼₖ` which is `[tⱼ, tⱼ₊ₖ₊₁)`, for `j = i - k, ..., i`.

## Arguments

  * `spline_dimension`
