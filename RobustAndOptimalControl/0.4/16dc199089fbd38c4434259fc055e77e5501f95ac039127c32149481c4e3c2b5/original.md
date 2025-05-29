```
loop_scale(L::LTISystem, w = 0)
```

Find the optimal diagonal scaling matrix `D` such that `D\L(iw)*D` has a minimized condition number at frequency `w`. Applicable to square `L` only. Use [`loop_scaling`](@ref) to obtain `D`.
