```
Y = change_representer(M::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, ::EuclideanMetric, p, X)
change_representer!(M::MetricManifold{ℝ,Euclidean{Tuple{2},ℝ},RosenbrockMetric}, Y, ::EuclideanMetric, p, X)
```

与えられたユークリッド勾配 `X` が `p` において、この関数は対応するリース表現者 `Y` を計算します。すなわち、$⟨X,Z⟩ = ⟨ Y, Z ⟩_{\mathrm{Rb},p}$ がすべての$Z$に対して成り立つように、言い換えれば$Y = G(p)^{-1}X$です。

この関数は、ユークリッド勾配をリーマン勾配に変換するために `riemannian_gradient` で使用されます。
