```
AlphaWarpedMetric{A} <: AbstractMetric
```

Is the alpha-warped metric on the Segre manifold, namely if

```
p = (lambda, x1, ..., xd) ∈ Seg(ℝ^n1 x ... x ℝ^nd) ~ ℝ^+ x S^(n1 - 1) x ... x S^(nd - 1)
```

and

```
u = (a, u1, ..., ud), v = (b, v1, ..., vd) ∈ T_p Seg(ℝ^n1 x ... x ℝ^nd)
```

then

```
⟨u, v⟩ := a * b + (alpha * lambda)^2 * (dot(u1, v1) + ... + dot(ud, vd)).
```

Example:

```
MetricManifold(Segre((2, 2, 3)), AlphaWarpedMetric{1.5}())
```
