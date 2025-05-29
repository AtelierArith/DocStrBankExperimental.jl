```
backtest(vms::Vector{<:VaRModel}, data::Vector{<:Real},
              windowsize::Integer;dataset_name::String="Dataset name not specified",
              lags::Integer=5)
```

Backtests a single `VaRModel` on the supplied dataset. `windowsize` specifies the number of in-sample observations used for forecasting Value-at-Risk. `backtest(...)` returns an object of type `BacktestResult`. The optional parameter `lags` controls the number of lags used in the the tests of time independence. `dataset_name` may be provided in order to be included in the `BacktestResult`
