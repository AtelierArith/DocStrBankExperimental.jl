```
project!(::MetricManifold{𝔽,<:Euclidean,ExtendedSymplecticMetric}, Y, p, X) where {𝔽}
```

Compute the projection of $X ∈ R^{2n×2n}$ onto $T_p\mathrm{Sp}(2n, ℝ)$ with respect to the [`RealSymplecticMetric`](@ref) $g$.

The closed form projection mapping is given by [GaoSonAbsilStykel:2021](@cite)

$$
  \operatorname{P}^{T_p\mathrm{Sp}(2n)}_{g_p}(X) = pJ_{2n}\operatorname{sym}(p^{\mathrm{T}}J_{2n}^{\mathrm{T}}X),
$$

where $\operatorname{sym}(A) = \frac{1}{2}(A + A^{\mathrm{T}})$ and and $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ denotes the [`SymplecticElement`](@ref).
