```
exp(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, X)
exp!(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g, X)
```

Compute the Lie group exponential of a vector `X` of the [`LieAlgebra`](@ref) of the circle group, represented as angles in $[-π, π)$. In that case, the Lie algebra is the real line and the Lie group exponential of a vector $X ∈ ℝ$ is its equivalence class

$$
    \exp(X) = [X] ∈ \bigl\{ [x] ∈ ℝ / 2πℤ\ \big|\ x ∈ [-π,π)\bigr \}.
$$

This can be computed in-place of `g`.
