```
inner(M::MetricManifold{ℝ, Segre{ℝ, V}, WarpedMetric{A}}, p, X, Y)
```

Inner product between two tangent vectors $X = (ν, u_1,…, u_d)$ and $Y = (ξ, v_1,…, v_d)$ at $p \doteq (λ, x_1,…, x_d)$:

$$
    ⟨X, Y⟩_{p} = ν ξ + (A λ)^2 (⟨ u_1, v_1 ⟩_{x_1} +… + ⟨u_d, v_d⟩_{x_d}),
$$

where $ν$, $ξ ∈ T_{λ} ℝ^{+} = ℝ$ and $u_i$, $v_i ∈ T_{x_i} \mathbb{S}^{n_i - 1} \subset ℝ^{n_i}$.
