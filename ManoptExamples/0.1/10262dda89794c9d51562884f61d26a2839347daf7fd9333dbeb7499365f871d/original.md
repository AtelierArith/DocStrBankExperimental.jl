```
X = log(::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, p, q)
log!(::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, X, p, q)
```

Compute the logarithmic map with respect to the [`RosenbrockMetric`](@ref ManoptExamples.RosenbrockMetric). The formula reads for any $j ∈ \{1,…,m\}$

$$
X = \begin{pmatrix}
  q_1 - p_1 \\
  q_2 - p_2 + (q_1 - p_1)^2
\end{pmatrix}
$$
