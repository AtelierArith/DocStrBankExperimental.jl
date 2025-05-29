```
evaluate_integral(f::UnivariateFunction,left::Real, right::Real)
evaluate_integral(f::UnivariateFunction,left::Union{Date,DateTime}, right::Union{Date,DateTime})
```

This calculates the integral of a function from a left limit to a right limit and returns a scalar.

If a `Date`, `DateTime` is input then it is first converted to a scalar with the `years_from_global_base` function.

### Inputs

  * `f` - A `UnivariateFunction`.
  * `left` - A left limit (scalar)
  * `right` - A right limit (scalar)

### Returns

  * A `Real`.
