```
inverse_local_metric(::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, p)
```

[`RosenbrockMetric`](@ref ManoptExamples.RosenbrockMetric)の局所計量行列の逆行列を、接空間$T_p\mathbb R^2$の標準単位ベクトル基底において次のように返します。

$$
G^{-1}_p =
\begin{pmatrix}
    1 & 2p_1\\
    2p_1 & 1+4p_1^2 \\
\end{pmatrix}.
$$
