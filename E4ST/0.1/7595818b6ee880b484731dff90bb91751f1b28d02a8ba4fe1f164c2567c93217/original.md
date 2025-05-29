```
parse_comparisons(row::DataFrameRow) -> pairs
```

Returns a set of pairs to be used in filtering rows of another table.  Looks for the following properties in the row:

  * `area, subarea` - if the row has a non-empty area and subarea, it will parse the comparison `row.area=>row.subarea`
  * `filter_` - if the row has any non-empty `filter_` (i.e. `filter1`, `filter2`) values, it will parse the comparison via [`parse_comparison`](@ref)
  * `genfuel` - if the row has a non-empty `genfuel`, it will add an comparion that checks that each row's `genfuel` equals this value
  * `gentype` - if the row has a non-empty `gentype`, it will add an comparion that checks that each row's `gentype` equals this value
  * `load_type` - if the row has a non-empty `load_type`, it will add an comparion that checks that each row's `load_type` equals this value
