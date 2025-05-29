```
project(G::SpecialLinear, p)
```

Project $p ∈ \mathrm{GL}(n, 𝔽)$ to the [`SpecialLinear`](@ref) group $G=\mathrm{SL}(n, 𝔽)$.

Given the singular value decomposition of $p$, written $p = U S V^\mathrm{H}$, the formula for the projection is

$$
\operatorname{proj}_{\mathrm{SL}(n, 𝔽)}(p) = U S D V^\mathrm{H},
$$

where

$$
D_{ij} = δ_{ij} \begin{cases}
    1            & \text{ if } i ≠ n \\
    \det(p)^{-1} & \text{ if } i = n
\end{cases}.
$$
