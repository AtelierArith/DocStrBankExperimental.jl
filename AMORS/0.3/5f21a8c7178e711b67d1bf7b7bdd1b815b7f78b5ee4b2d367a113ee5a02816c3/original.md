```
AMORS.has_converged(x, xp, tol) -> bool
```

yields whether the variables `x` has converged. Argument `xp` is the previous value of `x` and `tol ≥ 0` is a relative tolerance.

In the default implementation provided by AMORS for `x` and `xp` being arrays, the result is given by:

```
‖x - xp‖ ≤ tol⋅‖x‖
```

with `‖x‖` the Euclidean norm of `x`.

The method is expected to be extended for non-array types of `x` and `xp`. Another possibility is to specify the keyword `has_converged` in the call to [`AMORS.solve`](@ref) or [`AMORS.solve!`](@ref).
