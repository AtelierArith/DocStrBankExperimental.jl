```
Y = change_representer(M::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, ::EuclideanMetric, p, X)
change_representer!(M::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, Y, ::EuclideanMetric, p, X)
```

Given the Euclidean gradient `X` at `p`, this function computes the corresponding Riesz representer `Y``such that``⟨X,Z⟩ = ⟨ Y, Z ⟩_{\mathrm{Rb},p}``holds for all``Z``, in other words``Y = G(p)^{-1}X``.

this function is used in `riemannian_gradient` to convert a Euclidean into a Riemannian gradient.
