```
log(M::Segre{ℝ, V}, p, q)
```

Logarithmic map on the Segre manifold.

Let $p ≐ (λ, x_1, …, x_d)$, $q ≐ (μ, y_1, …, y_d) ∈ \mathcal{S}$. Assume $p$ and $q$ are connected by a geodesic.

Let

$$
    m = \sqrt{\sphericalangle(x_1, y_1)^2 + … + \sphericalangle(x_d, y_d)^2}
$$

and assume $(μ, y_1, …, y_d)$ is the representative of $q$ that minimizes $m$. Then

$$
    \operatorname{log}_p(q) =
    \left(
        \mu \cos{m} - \lambda,
        (y_1 - ⟨x_1, y_1⟩ x_1) \frac{\mu \sphericalangle(x_1, y_1) \sin{m}}{\lambda m \sin{\sphericalangle(x_1, y_1)}},
        \dots,
        (y_d - ⟨x_d, y_d⟩ x_d) \frac{\mu \sphericalangle(x_d, y_d) \sin{m}}{\lambda m \sin{\sphericalangle(x_d, y_d)}}
    \right).
$$

The formula is derived in theorem 4.4 in [JacobssonSwijsenVandervekenVannieuwenhoven:2024](@cite).
