```
AlphaWarpedMetric{A} <: AbstractMetric
```

アルファワープメトリックはセグレ多様体上にあり、すなわち

```
p = (lambda, x1, ..., xd) ∈ Seg(ℝ^n1 x ... x ℝ^nd) ~ ℝ^+ x S^(n1 - 1) x ... x S^(nd - 1)
```

および

```
u = (a, u1, ..., ud), v = (b, v1, ..., vd) ∈ T_p Seg(ℝ^n1 x ... x ℝ^nd)
```

ならば

```
⟨u, v⟩ := a * b + (alpha * lambda)^2 * (dot(u1, v1) + ... + dot(ud, vd)).
```

例:

```
MetricManifold(Segre((2, 2, 3)), AlphaWarpedMetric{1.5}())
```
