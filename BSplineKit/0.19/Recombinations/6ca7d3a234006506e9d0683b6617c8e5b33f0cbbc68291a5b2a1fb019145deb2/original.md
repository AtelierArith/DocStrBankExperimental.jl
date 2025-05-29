```
constraints(R::AbstractBSplineBasis) -> (left, right)
constraints(A::RecombineMatrix) -> (left, right)
```

Return the constraints (homogeneous boundary conditions) that the basis satisfies on each boundary.

Constraints are returned as a tuple `(left, right)` indicating the BCs that are satisfied on each boundary. Each element is a tuple of differential operators specifying the BCs.

For example, if both Dirichlet and Neumann BCs are satisfied on the left boundary, then `left = (Derivative(0), Derivative(1))`.

For non-recombined bases such as [`BSplineBasis`](@ref), this returns a tuple of empty tuples: `((), ())`, since no BCs are satisfied on either boundary.
