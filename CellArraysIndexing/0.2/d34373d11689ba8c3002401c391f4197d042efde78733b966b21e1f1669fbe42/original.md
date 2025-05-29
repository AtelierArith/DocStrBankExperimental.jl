```
getcellindex(A, cellᵢ, I)
```

Get the `cellᵢ` index of a specific cell in a `CellArray``.

# Arguments

  * `A::CPUCellArray{SVector, nDim, 1, T}`: The CPUCellArray to search in.
  * `cellᵢ::Int`: The index of the cell to retrieve.
  * `I::Vararg{Int, nDim}`: The indices of the elements within the cell.

# Returns

  * The index of the specified cell.
