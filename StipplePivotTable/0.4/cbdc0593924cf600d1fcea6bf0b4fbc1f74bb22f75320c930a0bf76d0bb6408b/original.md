```
Cell
```

A mutable struct representing a cell in a pivot table.

# Fields

  * `field::Union{String, Symbol}`: The field associated with the cell.
  * `sort_by::Union{String, Symbol}`: The criterion by which the cell is sorted. Defaults to `"label"`.
  * `order::Union{String, Symbol}`: The order of sorting. Can be `"asc"` for ascending or `"desc"` for descending. Defaults to `"asc"`.
  * `label::Union{String, Symbol}`: The label of the cell. Defaults to the value of `field`.

# Constructors

  * `Cell(field::Union{String, Symbol}; kwargs...)`: Create a new `Cell` instance with the specified `field` and optional keyword arguments for `sort_by`, `order`, and `label`.
