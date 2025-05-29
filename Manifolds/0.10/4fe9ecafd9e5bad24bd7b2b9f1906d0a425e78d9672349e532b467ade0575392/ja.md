```
inner(M::MetricManifold{ℝ, Segre{ℝ, V}, WarpedMetric{A}}, p, X, Y)
```

点$p \doteq (λ, x_1,…, x_d)$における2つの接ベクトル$X = (ν, u_1,…, u_d)$と$Y = (ξ, v_1,…, v_d)$の内積:

$$
    ⟨X, Y⟩_{p} = ν ξ + (A λ)^2 (⟨ u_1, v_1 ⟩_{x_1} +… + ⟨u_d, v_d⟩_{x_d}),
$$

ここで、$ν$, $ξ ∈ T_{λ} ℝ^{+} = ℝ$および$u_i$, $v_i ∈ T_{x_i} \mathbb{S}^{n_i - 1} \subset ℝ^{n_i}$です。
