```
setcell!(A, v::AbstractVector, I)
```

Set the value of a cell in a CPUCellArray to the value of `v::AbstractArray`.

# Arguments

  * `A::CellArray`: The CPUCellArray in which to set the cell value.
  * `v::AbstractVector`: The value to set the cell to.
  * `I::Vararg{Int, nDim}`: The indices of the cell to set.
