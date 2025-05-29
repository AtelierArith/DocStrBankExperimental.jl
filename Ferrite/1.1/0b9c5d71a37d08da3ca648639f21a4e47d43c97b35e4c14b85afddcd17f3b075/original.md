```
apply_zero!(K::SparseMatrixCSC, rhs::AbstractVector, ch::ConstraintHandler)
```

Adjust the matrix `K` and the right hand side `rhs` to account for prescribed Dirichlet boundary conditions and affine constraints such that `du = K \ rhs` gives the expected result (e.g. `du` zero for all prescribed degrees of freedom).

```
apply_zero!(v::AbstractVector, ch::ConstraintHandler)
```

Zero-out values in `v` corresponding to prescribed degrees of freedom and update values prescribed by affine constraints, such that if `a` fulfills the constraints, `a ± v` also will.

These methods are typically used in e.g. a Newton solver where the increment, `du`, should be prescribed to zero even for non-homogeneouos boundary conditions.

See also: [`apply!`](@ref).

# Examples

```julia
u = un + Δu                 # Current guess
K, g = assemble_system(...) # Assemble residual and tangent for current guess
apply_zero!(K, g, ch)       # Adjust tangent and residual to take prescribed values into account
ΔΔu = K \ g                # Compute the (negative) increment, prescribed values are "approximately" zero
apply_zero!(ΔΔu, ch)        # Make sure values are exactly zero
Δu .-= ΔΔu                  # Update current guess
```

!!! note
    The last call to `apply_zero!` is only strictly necessary for affine constraints. However, even if the Dirichlet boundary conditions should be fulfilled after `apply!(K, g, ch)`, solvers of linear systems are not exact. `apply!(ΔΔu, ch)` can be used to make sure the values for the prescribed degrees of freedom are fulfilled exactly.

