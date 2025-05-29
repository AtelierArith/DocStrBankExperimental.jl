```
left_integral(f::UnivariateFunction, right::Real)
left_integral(f::UnivariateFunction, right::Union{Date,DateTime})
```

This calculates the integral of a function from a right limit and returns it as a UnivariateFunction. So if you were to then evaluate this integral function at a point x then you would get the integral between right and x.

If a `Date`, `DateTime` is input then it is first converted to a scalar with the `years_from_global_base` function.

### Inputs

  * `f` - A `UnivariateFunction`.
  * `right` - A right limit (scalar)

### Returns

  * A `UnivariateFunction`.
