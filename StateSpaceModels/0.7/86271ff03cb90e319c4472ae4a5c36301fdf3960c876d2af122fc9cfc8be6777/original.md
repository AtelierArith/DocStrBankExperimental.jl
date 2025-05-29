```
auto_arima(y::Vector{Fl};
           seasonal::Int = 0,
           max_p::Int = 5,
           max_q::Int = 5,
           max_P::Int = 2,
           max_Q::Int = 2,
           max_d::Int = 2,
           max_D::Int = 1,
           max_order::Int = 5,
           information_criteria::String = "aicc",
           allow_mean::Bool = true,
           show_trace::Bool = false,
           integration_test::String = "kpss",
           seasonal_integration_test::String = "seas"
           ) where Fl
```

Automatically fits the best [`SARIMA`](@ref) model according to the best information criteria 

# TODO write example

# References

  * Hyndman, RJ and Khandakar.

Automatic time series forecasting: The forecast package for R. Journal of Statistical Software, 26(3), 2008.
