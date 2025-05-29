```
project(::SymplecticMatrices, p, A)
project!(::SymplecticMatrices, Y, p, A)
```

Given a point $p \in \mathrm{Sp}(2n)$, project an element $A \in ℝ^{2n×2n}$ onto the tangent space $T_p\mathrm{Sp}(2n)$ relative to the euclidean metric of the embedding $ℝ^{2n×2n}$.

That is, we find the element $X \in T_p\operatorname{Sp}(2n)$ which solves the constrained optimization problem

$$
    \operatorname{min}_{X \in ℝ^{2n×2n}} \frac{1}{2}\lVert X - A\rVert^2, \quad
    \text{such that}\;
    h(X) := X^{\mathrm{T}} J_{2n} p + p^{\mathrm{T}} J_{2n} X = 0,
$$

where $h: ℝ^{2n×2n} → \operatorname{skew}(2n)$ denotes the restriction of $X$ onto the tangent space $T_p\operatorname{SpSt}(2n, 2k)$ and $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ denotes the [`SymplecticElement`](@ref).
