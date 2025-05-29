```
CellRange <: AbstractCellRange
```

Defines a range of cells in a specified [`Domain`](@ref) as a linear list.

# Fields

  * `domain`
  * `operatorID`
  * `indices`: may be any valid Julia indexing range thing eg 1:100, [1 2 3 4], etc
