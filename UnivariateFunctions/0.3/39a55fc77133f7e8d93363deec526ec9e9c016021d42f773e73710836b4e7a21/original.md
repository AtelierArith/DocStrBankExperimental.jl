```
evaluate(f::UnivariateFunction, r::Real)
evaluate(f::UnivariateFunction, d::Union{Date,DateTime})
evaluate(f::UnivariateFunction, x::DatePeriod)
```

This evaluates the function at the requested point. If a `Date`, `DateTime` is input then it is first converted to a scalar with the `years_from_global_base` function. `DatePeriod`s are converted with the `period_length` function.
