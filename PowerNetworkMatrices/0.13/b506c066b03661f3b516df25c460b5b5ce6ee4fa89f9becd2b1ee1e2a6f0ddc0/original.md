```julia
Ybus(branches, buses; ...)
Ybus(
    branches,
    buses,
    fixed_admittances;
    check_connectivity,
    make_branch_admittance_matrices
)

```

Builds a Ybus from a collection of buses and branches. The return is a Ybus Array indexed with the bus numbers and the branch names.

# Arguments

  * `check_connectivity::Bool`: Checks connectivity of the network using Depth First Search (DFS)
