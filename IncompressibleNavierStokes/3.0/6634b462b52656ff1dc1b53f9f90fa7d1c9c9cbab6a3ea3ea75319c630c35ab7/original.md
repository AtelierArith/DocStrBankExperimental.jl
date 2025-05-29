```julia
Qfield(u, setup) -> Any

```

Compute $Q$-field [Jeong1995](@cite) given by

$$
Q = - \frac{1}{2} \sum_{α, β} \frac{\partial u^α}{\partial x^β}
\frac{\partial u^β}{\partial x^α}.
$$

Differentiable version.
