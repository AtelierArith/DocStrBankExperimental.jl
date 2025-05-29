```
function SortedDataFrame(
    df::DataFrame,
    time::Symbol,
    grouping::Symbol,
    value::Symbol,
    time_period_per_unit::Dates.Period,
)

SortedDataFrame(
    df::DataFrame,
    timevar::Symbol,
    groupingvar::Symbol,
    valuevar::Symbol,
    dic::Dict{Symbol,Vector{I}},
    vol_unit::Dates.Period,
) where I<:Integer

SortedDataFrame(
    ts::SortedDataFrame{I},
    timevar::Symbol,
    groupingvar::Symbol,
    valuevar::Symbol,
    vol_unit::Dates.Period,
) where I<:Integer
```

This struct wraps a `DataFrame`. In the constructor function for the dataframe we presort the data and create a mapping dict so that it is fast to subset the DataFrame by the group.

For the constructor pass in the dataframe, name of time column, name of grouping  column and name of value column to the constructor.

### Inputs

  * `df` - The tick data
  * `time` - The column of the data representing time.
  * `grouping` - The column of the data representing the asset name
  * `value` - The column of the data representing price/logprice/etc.
  * `time_period_per_unit` - The period that one unit (in the time column) corresponds to.

### Returns

  * A `SortedDataFrame`.
