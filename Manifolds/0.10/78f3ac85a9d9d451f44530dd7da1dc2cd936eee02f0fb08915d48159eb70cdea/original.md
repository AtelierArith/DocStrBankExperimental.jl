```
exp(M::MetricManifold{ℝ, Segre{ℝ, V}, WarpedMetric{A}}, p, X)
```

Exponential map on the warped Segre manifold.

Let $p ≐ (λ, x_1,…, x_d) ∈ \mathcal{S}_A$ and $X = (ν, u_1,…, u_d) ∈ T_p \mathcal{S}_A$. Then the exponential map is given by

$$
    \operatorname{exp}_p(X) ≐
    \left(
        \sqrt{(λ + ν)^2 + (λ A m)^2},\\
        x_1 \cos\mathopen{\Big(} \frac{f \lVert u_1 \rVert_{x_1}}{A m} \mathclose{\Big)} + \frac{u_1}{\lVert u_1 \rVert_{x_1}} \sin\mathopen{\Big(} \frac{f \lVert u_1 \rVert_{x_1}}{A m} \mathclose{\Big)},\\
        …,\\
        x_d \cos\mathopen{\Big(} \frac{f \lVert u_d \rVert_{x_d}}{A m} \mathclose{\Big)} + \frac{u_d}{\lVert u_d \rVert_{x_d}} \sin\mathopen{\Big(} \frac{f \lVert u_d \rVert_{x_d}}{A m} \mathclose{\Big)}
    \right),
$$

where

$$
    \begin{aligned}
        f &= \frac{\pi}{2} - \tan^{-1}\mathopen{\Big(} \frac{λ + ν}{λ A m} \mathclose{\Big)},\\
        m &= \sqrt{\lVert u_1 \rVert_{x_1}^2 + … + \lVert u_d \rVert_{x_d}^2}.
    \end{aligned}
$$

If $m = 0$ and $-λ < ν$, then $\operatorname{exp}_p(v) = p + X$.

The formula is derived in proposition 3.1 in [JacobssonSwijsenVandervekenVannieuwenhoven:2024](@cite).
