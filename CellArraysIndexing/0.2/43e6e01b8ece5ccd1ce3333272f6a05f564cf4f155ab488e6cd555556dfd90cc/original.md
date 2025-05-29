```
getcell(A, I)
```

Get the cell at the specified indices `I` from the CellArray `A`.

# Arguments

  * `A::CellArray`: The CPUCellArray from which to retrieve the cell.
  * `I::Vararg{Int, nDim}`: The indices specifying the position of the cell in the CPUCellArray.

# Returns

  * The cell at the specified indices `I`.
