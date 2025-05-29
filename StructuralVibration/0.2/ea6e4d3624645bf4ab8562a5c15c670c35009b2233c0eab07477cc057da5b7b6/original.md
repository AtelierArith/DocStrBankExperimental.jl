```
gradient(f::Vector{Real}, t; method = :cubic)
gradient(f::Matrix{Real}, t; method = :cubic, dims = 1)
```

Compute the gradient of a function `f` at points `t`.

**Inputs**

  * `f`: Function values
  * `t`: Points at which to evaluate the gradient
  * `method`: Interpolation method

      * `:linear`: Linear interpolation
      * `:cubic`: Cubic spline interpolation (default)
  * `dims`: Dimension along which to compute the gradient

      * `1`: Rows (default)
      * `2`: Columns

**Output**

  * `df`: Gradient of the vector `f` at points `t`

**Note**

If `method` is `:cubic`, `t` must be an `AbstractRange`.
