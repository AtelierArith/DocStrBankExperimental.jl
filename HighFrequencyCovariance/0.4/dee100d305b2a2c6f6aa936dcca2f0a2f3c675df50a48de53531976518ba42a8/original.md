```
subset_to_time(ts::SortedDataFrame, totime::Real)
```

This subsets a `SortedDataFrame` to only the first observations up until some time.

### Inputs

  * `ts` - Tick data.
  * `totime` - Up to what time.

### Returns

  * A (smaller) `SortedDataFrame`.
