```
DataFrames.combine(
    dfs::Vector{SortedDataFrame{<:Integer}};
    timevar::Symbol = dfs[1].time,
    groupingvar::Symbol = dfs[1].grouping,
    valuevar::Symbol = dfs[1].value,
    period::Dates.Period = dfs[1].time_period_per_unit,
)
```

Combine a vector of data frames

### Inputs

  * `dfs` - A vector of SortedDataFrames
  * `timevar` - The desired name of the column representing time.
  * `groupingvar` - The desired name of the column representing the asset name
  * `valuevar` - The desired name of the column representing price/logprice/etc.
  * `period` - The desired period that one unit (in the time column) corresponds to.
