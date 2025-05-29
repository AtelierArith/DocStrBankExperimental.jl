```
apply!(K::SparseMatrixCSC, rhs::AbstractVector, ch::ConstraintHandler)
```

Adjust the matrix `K` and right hand side `rhs` to account for the Dirichlet boundary conditions specified in `ch` such that `K \ rhs` gives the expected solution.

!!! note
    `apply!(K, rhs, ch)` essentially calculates

    ```julia
    rhs[free] = rhs[free] - K[constrained, constrained] * a[constrained]
    ```

    where `a[constrained]` are the inhomogeneities. Consequently, the sign of `rhs` matters (in contrast with `apply_zero!`).


```julia
apply!(v::AbstractVector, ch::ConstraintHandler)
```

Apply Dirichlet boundary conditions and affine constraints, specified in `ch`, to the solution vector `v`.

# Examples

```julia
K, f = assemble_system(...) # Assemble system
apply!(K, f, ch)            # Adjust K and f to account for boundary conditions
u = K \ f                   # Solve the system, u should be "approximately correct"
apply!(u, ch)               # Explicitly make sure bcs are correct
```

!!! note
    The last operation is not strictly necessary since the boundary conditions should already be fulfilled after `apply!(K, f, ch)`. However, solvers of linear systems are not exact, and thus `apply!(u, ch)` can be used to make sure the boundary conditions are fulfilled exactly.

