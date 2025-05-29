```
compute_lodf(system, branch_names_out) -> KeyedArray
compute_lodf(system::System, ptdf_matrix, branch_names_out) -> KeyedArray
compute_lodf(buses, branches, ptdf, branch_names_out) -> KeyedArray
```

Returns the `M*O` DC-Line Outage Distribution Factor (DC-LODF) matrix of the network.

**Important Note:** In the current implementation, we use `lodf` only if the contingency scenario does not have any line coming in service. We can also use this function if we want to ignore the lines coming in service.

# Inputs

  * `buses::Buses`
  * `branches::Branches`
  * `ptdf_matrix`: The pre-calculated PTDF matrix of the system
  * `branch_names_out`: The names of the branches that are going out in the contingency scenario.

# Output

  * The LODF matrix as a `KeyedArray`. The axes are the branch names and `branch_names_out`.

!!! note
    The resulting LODF matrix is sensitive to the input PTDF matrix. Using a thresholded PTDF as input might lead to imprecisions in constrast to using the full PTDF.

