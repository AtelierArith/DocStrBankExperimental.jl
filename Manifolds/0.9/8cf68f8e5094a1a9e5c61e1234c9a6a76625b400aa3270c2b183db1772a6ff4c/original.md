```
project(G::SpecialLinear, p, X)
```

Orthogonally project $X ∈ 𝔽^{n×n}$ onto the tangent space of $p$ to the [`SpecialLinear`](@ref) $G = \mathrm{SL}(n, 𝔽)$. The formula reads

$$
\operatorname{proj}_{p}
    = (\mathrm{d}L_p)_e ∘ \operatorname{proj}_{𝔰𝔩(n, 𝔽)} ∘ (\mathrm{d}L_p^{-1})_p
    \colon X ↦ X - \frac{\operatorname{tr}(X)}{n} I,
$$

where the last expression uses the tangent space representation as the Lie algebra.
