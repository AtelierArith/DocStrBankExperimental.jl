```
local_metric(::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, p)
```

Return the local metric matrix of the [`RosenbrockMetric`](@ref ManoptExamples.RosenbrockMetric) in the canonical unit vector basis of the tangent space $T_p\mathbb R^2$ given as

$$
G_p = \begin{pmatrix}
  1+4p_1^2 & -2p_1 \\
  -2p_1 & 1
\end{pmatrix}
$$
