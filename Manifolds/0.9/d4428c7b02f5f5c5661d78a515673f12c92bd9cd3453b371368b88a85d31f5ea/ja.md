```
project!(::MetricManifold{𝔽,<:Euclidean,ExtendedSymplecticMetric}, Y, p, X) where {𝔽}

$X ∈ R^{2n×2n}$ の $T_p\mathrm{Sp}(2n, ℝ)$ への射影を [`RealSymplecticMetric`](@ref) $g$ に関して計算します。

閉じた形の射影写像は [GaoSonAbsilStykel:2021](@cite) によって与えられます。

```

math   \operatorname{P}^{T*p\mathrm{Sp}(2n)}*{g*p}(X) = pJ*{2n}\operatorname{sym}(p^{\mathrm{T}}J_{2n}^{\mathrm{T}}X),

```

ここで、$\operatorname{sym}(A) = \frac{1}{2}(A + A^{\mathrm{T}})$ であり、$J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ は [`SymplecticElement`](@ref) を示します。
```
