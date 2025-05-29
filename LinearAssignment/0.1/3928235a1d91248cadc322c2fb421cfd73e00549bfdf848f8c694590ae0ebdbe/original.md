```
linear_assignment!(
    L::LAWorkspaceCSC{Tv},
    cost::SparseMatrixCSC{Tc},
    early_exit::Bool = true,
    reset::Bool = true
) -> LAWorkspaceCSC{Tv}

linear_assignment!(
    L::LAWorkspaceCSC{Tv},
    m::Integer,
    n::Integer,
    colptr::AbstractVector{<:Integer},
    rowval::AbstractVector{<:Integer},
    nzval::AbstractVector{Tc},
    early_exit::Bool = true,
    reset::Bool = true
) -> LAWorkspaceCSC{Tv}
```

Solve the sparse linear assignment problem using a modified Jonker-Volgenant algorithm [1].

The cost of the assignment can be computed using `compute_cost(L, cost)`, `compute_cost(L, m, n, colptr, rowval, nzval)`. The assigned row and column indices can be found in LAWorkspaceCSC.I,J, respectively.

### Arguments

  * `L::LAWorkspaceCSC{Tv}`: workspace struct
  * `cost::SparseMatrixCSC{Tc}`: sparse rectangular cost matrix
  * `early_exit::Bool = true`: exit as soon as infeasibility is detected
  * `reset::Bool = true`: zero out assigned indices and dual vectors

### Returns

  * `LAWorkspaceCSC{T}`: struct containing assigned indices, dual vectors, and more.

### References

[1] DF Crouse. On implementing 2D rectangular assignment algorithms.     IEEE Transactions on Aerospace and Electronic Systems, 52(4):1679-1696,     August 2016, DOI:10.1109/TAES.2016.140952
