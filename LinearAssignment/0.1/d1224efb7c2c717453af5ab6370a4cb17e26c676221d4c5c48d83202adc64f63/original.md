```
linear_assignment(
    cost::Union{SMatrix{M, N, T}, MMatrix{M, N, T}},
    early_exit::Bool = true
) -> Tuple{
    SVector{N, UInt8},  # assigned row indices for columns, cost[I[j], j]
    SVector{M, UInt8},  # assigned column indices for rows, cost[i, J[i]]
    SVector{M, T},      # dual row variables
    SVector{N, T},      # dual column variables
    Bool                # feasible assignment
}
```

Solve the linear assignment problem using a modified Jonker-Volgenant algorithm [1].

The cost of the assignment can be computed using `compute_cost(cost, I)`.

### Arguments

  * `cost::Union{SMatrix{M, N, T}, MMatrix{M, N, T}}`: rectangular cost matrix
  * `early_exit::Bool = true`: exit as soon as infeasibility is detected

### Returns

  * `SVector{N, UInt8}`: assigned row indices for columns
  * `SVector{M, UInt8}`: assigned column indices for rows
  * `SVector{M, T}`: dual row variables
  * `SVector{N, T}`: dual column variables
  * `Bool`: is assignment feasible

### References

[1] DF Crouse. On implementing 2D rectangular assignment algorithms.     IEEE Transactions on Aerospace and Electronic Systems, 52(4):1679-1696,     August 2016, DOI:10.1109/TAES.2016.140952
