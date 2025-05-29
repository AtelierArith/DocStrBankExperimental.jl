```
ons(timeseries::String="L522", dataset::String="MM23")::TimeArray
```

The ons() method is a wrapper to download financial and economic time series data from the Office for National Statistics (ONS).

The ons() method takes two string arguments corresponding to a dataset and timeseries code from  the ONS database, to explore the database, you can use https://www.ons.gov.uk/timeseriestool. It returns the data in the TimeSeries.TimeArray data structure with additional information in the meta field. The data might include monthly values, quarterly averages and yearly averages, with column names monthly, quarterly and yearly. The timestamps are the first day of the period.  When no argument is provided, the default dataset  is the Consumer Price Index including housing costs (CPIH) which is the ONS’s headline measure of inflation.

# Examples

```julia
UK_RPI = ("CHAW","MM23")
UK_CPI = ("D7BT","MM23")
UK_CPIH = ("L522","MM23")
```

# References

https://www.ons.gov.uk/timeseriestool

# See Also

  * fred() which accesses the St. Louis Federal Reserve financial and economic data sets.
  * yahoo() which is a wrapper from downloading financial time series for stocks from Yahoo Finance.
