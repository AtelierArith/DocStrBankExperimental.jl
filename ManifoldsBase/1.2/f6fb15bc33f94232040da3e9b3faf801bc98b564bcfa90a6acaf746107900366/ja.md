```
Y = Weingarten(M::ProductManifold, p, X, V)
Weingarten!(M::ProductManifold, Y, p, X, V)
```

メトリックが分離されるため、Weingarten写像 $\mathcal W_p$ の計算も [`ProductManifold`](@ref) `M` の単一要素に対して要素ごとに計算できます。
