```
yearfrac(startdate::Date, enddate::Date, dc::DayCount)
```

Compute the fractional number of years between `startdate` and `enddate`, according to the [`DayCount` object](@ref daycount_types) `dc`.

  * If `startdate == enddate`, then the result is zero.
  * If `startdate > enddate`, then the result is `-yearfrac(enddate, startdate, dc)`.
