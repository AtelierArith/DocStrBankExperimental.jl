```
inner(M::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, p, X, Y)
```

Compute the inner product on $\mathbb R^2$ with respect to the [`RosenbrockMetric`](@ref RosenbrockMetric), i.e. for $X,Y \in T_p\mathcal M$ we have

$$
⟨X,Y⟩_{\mathrm{Rb},p} = X^\mathrm{T}G_pY, \qquad
G_p = \begin{pmatrix}
  1+4p_1^2 & -2p_1\\
  -2p_1 & 1
\end{pmatrix},
$$
