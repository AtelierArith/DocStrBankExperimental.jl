```
yearfrac(p::AbstractTime)
```

Compute the ACT/365 year fraction from a `Period` object (e.g., `Year(1)`, `Day(180)`). It allows also for `CompoundPeriod`, and even Dates, interpreting them as time periods from year 0 of the Gregorian calendar. Calculates the duration represented by the period in milliseconds and divides by `MILLISECONDS_IN_YEAR_365`.
