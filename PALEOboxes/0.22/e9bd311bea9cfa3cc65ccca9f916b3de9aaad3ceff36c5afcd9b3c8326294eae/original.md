```
CellRangeColumns <: AbstractCellRange
```

Defines a range of cells in a specified [`Domain`](@ref), organised by `columns`.

# Fields

  * `domain`
  * `operatorID`
  * `indices`: iterator through all cells in arbitrary order
  * `columns`: iterator through columns: columns[n] returns a Pair icol=>cells where cells are ordered top to bottom
