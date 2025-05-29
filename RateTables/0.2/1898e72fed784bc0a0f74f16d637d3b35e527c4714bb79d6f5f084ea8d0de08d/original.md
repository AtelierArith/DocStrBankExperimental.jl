```
daily_hazard(rt::BasicRateTable, age, date)
daily_hazard(rt::RateTable,      age, date, args...)
daily_hazard(rt::RateTable,      age, date; kwargs...)
```

This function queries daily hazard values from a given BasicRateTable. The parameters `age` and `date` have to be in days (1 year = 365.241 days). Potential args and kwargs will be used to subset the ratetable.
