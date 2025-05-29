```
project(::SymplecticStiefel, p, A)
project!(::SymplecticStiefel, Y, p, A)
```

Given a point $p ∈ \mathrm{SpSt}(2n, 2k)$, project an element $A ∈ ℝ^{2n×2k}$ onto the tangent space $T_p\mathrm{SpSt}(2n, 2k)$ relative to the euclidean metric of the embedding $ℝ^{2n×2k}$.

That is, we find the element $X ∈ T_p\mathrm{SpSt}(2n, 2k)$ which solves the constrained optimization problem

$$
    \displaystyle\operatorname{min}_{X ∈ ℝ^{2n×2k}} \frac{1}{2}||X - A||^2, \quad
    \text{s.t.}\;
    h(X) := X^{\mathrm{T}} J p + p^{\mathrm{T}} J X = 0,
$$

where $h : ℝ^{2n×2k} → \operatorname{skew}(2k)$ defines the restriction of $X$ onto the tangent space $T_p\mathrm{SpSt}(2n, 2k)$.
