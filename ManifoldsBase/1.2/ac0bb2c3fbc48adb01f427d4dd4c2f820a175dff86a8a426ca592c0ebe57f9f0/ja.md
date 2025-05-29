```
Y = Weingarten(M::AbstractPowerManifold, p, X, V)
Weingarten!(M::AbstractPowerManifold, Y, p, X, V)
```

メトリックが分離されるため、Weingarten写像 $\mathcal W_p$ の計算も [`PowerManifold`](@ref) `M` の各要素に対して要素ごとに計算できます。
