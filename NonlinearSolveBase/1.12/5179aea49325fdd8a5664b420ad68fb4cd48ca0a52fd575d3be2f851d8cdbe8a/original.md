```
DampedNewtonDescent(; linsolve = nothing, initial_damping, damping_fn)
```

A Newton descent algorithm with damping. The damping factor is computed using the `damping_fn` function. The descent direction is computed as $(JᵀJ + λDᵀD) δu = -fu$. For non-square Jacobians, we default to solving for `Jδx = -fu` and `√λ⋅D δx = 0` simultaneously. If the linear solver can't handle non-square matrices, we use the normal form equations $(JᵀJ + λDᵀD) δu = Jᵀ fu$. Note that this factorization is often the faster choice, but it is not as numerically stable as the least squares solver.

The damping factor returned must be a non-negative number.

### Keyword Arguments

  * `initial_damping`: the initial damping factor to use
  * `damping_fn`: the function to use to compute the damping factor. This must satisfy the [`NonlinearSolveBase.AbstractDampingFunction`](@ref) interface.
