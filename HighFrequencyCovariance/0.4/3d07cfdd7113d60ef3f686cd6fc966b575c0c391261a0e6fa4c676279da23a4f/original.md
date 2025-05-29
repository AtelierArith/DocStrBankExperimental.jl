```
duration(ts::SortedDataFrame; in_dates_period::Bool = true)
```

The time elapsed between the first and the last tick in a `SortedDataFrame`.

### Inputs

  * `ts` - Tick data.
  * `in_dates_period` - In Dates.Period format or just a number for the numeric difference between first and last tick.

### Returns

  * A scalar representing this duration.
