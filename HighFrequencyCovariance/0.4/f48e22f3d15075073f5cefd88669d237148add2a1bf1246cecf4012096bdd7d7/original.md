```
subset_to_tick(ts::SortedDataFrame, n::Integer)
```

This subsets a `SortedDataFrame` to only the first n ticks.

### Inputs

  * `ts` - Tick data.
  * `n` - How many ticks to subset to.

### Returns

  * A (smaller) `SortedDataFrame`.
