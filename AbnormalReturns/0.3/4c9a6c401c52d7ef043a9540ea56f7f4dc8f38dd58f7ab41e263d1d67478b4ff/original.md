```
var[std](rr::Union{AbstractVector{<:RegressionModel}, RegressionModel})
var[std](data::Union{IterateFixedTable, FixedTable}; minobs=0.8)
```

If a regression model is passed, then this calculates the variance (standard deviation) based on the residual sum of squares divided by the degrees of freedom. A vector of RegressionModel will return the same length of vector results.

If a FixedTable is passed (or an IterateFixedTable), and that contains only one column, then the variance (standard deviation) is calculated for that column. If it has two columns, then the calculation is based on the difference between the columns.
