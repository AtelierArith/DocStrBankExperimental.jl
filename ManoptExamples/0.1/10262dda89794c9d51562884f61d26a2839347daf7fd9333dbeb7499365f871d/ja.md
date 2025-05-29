```
X = log(::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, p, q)
log!(::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, X, p, q)
```

[`RosenbrockMetric`](@ref ManoptExamples.RosenbrockMetric)に関する対数写像を計算します。式は任意の $j ∈ \{1,…,m\}$ に対して次のようになります。

$$
X = \begin{pmatrix}
  q_1 - p_1 \\
  q_2 - p_2 + (q_1 - p_1)^2
\end{pmatrix}
$$
