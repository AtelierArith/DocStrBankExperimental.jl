```
local_metric(::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, p)
```

ローカルメトリック行列を返します [`RosenbrockMetric`](@ref ManoptExamples.RosenbrockMetric) の接空間 $T_p\mathbb R^2$ の標準単位ベクトル基底において、次のように与えられます

$$
G_p = \begin{pmatrix}
  1+4p_1^2 & -2p_1 \\
  -2p_1 & 1
\end{pmatrix}
$$
