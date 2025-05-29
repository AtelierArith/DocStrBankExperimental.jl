```
PivotTableOptions
```

A mutable struct that holds options for configuring a pivot table.

# Fields

  * `rows::Vector{Cell}`: A vector of `Cell` objects representing the rows of the pivot table. Defaults to an empty vector.
  * `columns::Vector{Cell}`: A vector of `Cell` objects representing the columns of the pivot table. Defaults to an empty vector.
  * `values::Vector{Value}`: A vector of `Value` objects representing the values in the pivot table. Defaults to an empty vector.
  * `filters::Vector{Filter}`: A vector of `Filter` objects representing the filters applied to the pivot table. Defaults to an empty vector.
