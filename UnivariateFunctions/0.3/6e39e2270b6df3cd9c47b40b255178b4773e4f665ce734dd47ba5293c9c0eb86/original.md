```
right_integral(f::UnivariateFunction, left::Real)
right_integral(f::UnivariateFunction, left::Union{Date,DateTime})
```

This calculates the integral of a function from a left limit and returns it as a UnivariateFunction. So if you were to then evaluate this integral function at a point x then you would get the integral between left and x.

If a `Date`, `DateTime` is input then it is first converted to a scalar with the `years_from_global_base` function.

### Inputs

  * `f` - A `UnivariateFunction`.
  * `left` - A left limit (scalar)

### Returns

  * A `UnivariateFunction`.
