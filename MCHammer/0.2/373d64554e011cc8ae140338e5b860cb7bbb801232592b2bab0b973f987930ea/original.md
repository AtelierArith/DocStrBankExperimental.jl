```
trend_chrt(SimTimeArray, PeriodRange::Vector{Date}; x_label="periods", quantiles=[0.05,0.5,0.95])
```

Visualizes a simulated time series with confidence bands. PeriodRange must be a vector of Dates (e.g., using Dates: `collect(Date(2019,1,1):Year(1):Date(2023,1,1))`).
