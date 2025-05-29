```
auto_ets(y::Vector{Fl}; seasonal::Int = 0) where Fl
```

Automatically fits the best [`ExponentialSmoothing`](@ref) model according to the best AIC  between the models:

  * ETS(A, N, N)
  * ETS(A, A, N)
  * ETS(A, Ad, N)

If the user provides the time series seasonality it will search between the models

  * ETS(A, N, A)
  * ETS(A, A, A)
  * ETS(A, Ad, A)

# References

  * Hyndman, Robin John; Athanasopoulos, George.

Forecasting: Principles and Practice.   2nd ed. OTexts, 2018.
