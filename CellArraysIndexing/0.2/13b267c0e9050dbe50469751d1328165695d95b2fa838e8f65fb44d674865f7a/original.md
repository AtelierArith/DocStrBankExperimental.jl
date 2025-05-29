```
setcellindex!(A, v, cellᵢ, I)
```

Set the `cellᵢ` index of a specific cell in a `CellArray``to the value of the scalar`v`.

# Arguments

  * `A::CPUCellArray{SVector, nDim, 1, T}`: The CPUCellArray to search in.
  * `v<:Real`: new value of the cell index.
  * `cellᵢ::Int`: The index of the cell to retrieve.
  * `I::Vararg{Int, nDim}`: The indices of the elements within the cell.

# Returns

  * The index of the specified cell.
