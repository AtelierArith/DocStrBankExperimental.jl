```
inner(M::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, p, X, Y)
```

$$
\mathbb R^2
$$

における[`RosenbrockMetric`](@ref RosenbrockMetric)に関する内積を計算します。すなわち、$X,Y \in T_p\mathcal M$に対して次のようになります。

$$
⟨X,Y⟩_{\mathrm{Rb},p} = X^\mathrm{T}G_pY, \qquad
G_p = \begin{pmatrix}
  1+4p_1^2 & -2p_1\\
  -2p_1 & 1
\end{pmatrix},
$$
