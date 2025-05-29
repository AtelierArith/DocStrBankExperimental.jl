```
linear_assignment(
    cost::SparseMatrixCSC{Tv},
    early_exit::Bool = true
) -> LAWorkspaceCSC{Tv}
```

Solve the sparse linear assignment problem using a modified Jonker-Volgenant algorithm [1].

The cost of the assignment can be computed using `compute_cost(L, cost)`. The assigned row and column indices can be found in LAWorkspaceCSC.I,J, respectively.

### Arguments

  * `cost::SparseMatrixCSC{Tv}`: sparse rectangular cost matrix
  * `early_exit::Bool = true`: exit as soon as infeasibility is detected

### Returns

  * `LAWorkspaceCSC{Tv}`: struct containing assigned indices, dual vectors, and more.

### References

[1] DF Crouse. On implementing 2D rectangular assignment algorithms.     IEEE Transactions on Aerospace and Electronic Systems, 52(4):1679-1696,     August 2016, DOI:10.1109/TAES.2016.140952
