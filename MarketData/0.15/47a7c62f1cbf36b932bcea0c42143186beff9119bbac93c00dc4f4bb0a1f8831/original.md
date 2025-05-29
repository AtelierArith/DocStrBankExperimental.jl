fred(data::String="CPIAUCNS")::TimeArray

The fred() method is a wrapper to download financial and economic time series data from the St. Louis Federal Reserve (FRED).

The fred() method takes a string argument that corresponds to a series code from the St. Louis Federal Reserve (FRED) database. It returns the data in the TimeSeries.TimeArray data structure.  When no argument is provided, the default data set is the Consumer Price Index for All Urban Consumers: All Items (CPIAUCNS).

# Examples

```julia
DGS = fred("DGS10")
CPI = fred()
```

# References

https://research.stlouisfed.org/fred2

# See Also

  * yahoo() which is a wrapper to download financial time series for stocks from Yahoo Finance.
  * ons()   which is a wrapper to download financial and economic time series data from the Office for National Statistics (ONS).
