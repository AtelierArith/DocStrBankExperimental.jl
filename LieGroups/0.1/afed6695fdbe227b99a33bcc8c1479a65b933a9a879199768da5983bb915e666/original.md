```
log(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g)
log!(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, X, g)
```

Compute the Lie group logarithm on the [`CircleGroup`](@ref circle-group-real), represented as angles in $[-π,π)$. The [`LieAlgebra`](@ref) is the real line and $\log$ is given by the identity map.

Formally $\log$ promotes an equivalence class $[X]$ to a representative $X∈ℝ$.

This can be computed in-place of `X`.
