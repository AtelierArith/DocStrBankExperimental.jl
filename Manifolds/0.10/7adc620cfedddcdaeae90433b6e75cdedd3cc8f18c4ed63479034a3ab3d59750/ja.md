```
log(M::MetricManifold{ℝ, Segre{ℝ,V}, WarpedMetric{A}}, p, q)
```

歪んだセグレ多様体上の対数写像。

$$
p ≐ (λ, x_1,…, x_d)
$$

、$q ≐ (μ, y_1,…, y_d) ∈ \mathcal{S}_A$ とします。$p$ と $q$ が測地線で接続されていると仮定します。次のように定義します。

$$
    m = \sqrt{\sphericalangle(x_1, y_1)^2 +… + \sphericalangle(x_d, y_d)^2}
$$

そして $(μ, y_1,…, y_d)$ が $m$ を最小化する $q$ の代表であると仮定します。すると、

$$
    \operatorname{log}_p(q) =
    \left(
        \mu \cos{m} - \lambda,
        (y_1 - ⟨x_1, y_1⟩ x_1) \frac{\mu \sphericalangle(x_1, y_1) \sin(A m)}{\lambda A m \sin{\sphericalangle(x_1, y_1)}},
        \dots,
        (y_d - ⟨x_d, y_d⟩ x_d) \frac{\mu \sphericalangle(x_d, y_d) \sin(A m)}{\lambda A m \sin{\sphericalangle(x_d, y_d)}}
    \right).
$$

この公式は [JacobssonSwijsenVandervekenVannieuwenhoven:2024](@cite) の定理 4.4 で導出されています。
