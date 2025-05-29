```
loop_scaling(M0::Matrix, tol = 0.0001)
```

Find the optimal diagonal scaling matrix `D` such that `D\M0*D` has a minimized condition number. Applicable to square `M0` only. See also [`structured_singular_value`](@ref) with option `dynamic=true`. Use [`loop_scale`](@ref) to find and apply the scaling to a loop-transfer function.
