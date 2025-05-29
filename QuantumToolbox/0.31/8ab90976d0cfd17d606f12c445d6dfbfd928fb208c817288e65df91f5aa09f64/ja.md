```
tracedist(ρ::QuantumObject, σ::QuantumObject)
```

2つの[`QuantumObject`](@ref)間の[トレース距離](https://en.wikipedia.org/wiki/Trace_distance)を計算します: $T(\hat{\rho}, \hat{\sigma}) = \frac{1}{2} \lVert \hat{\rho} - \hat{\sigma} \rVert_1$

`ρ`と`σ`は、いずれかが[`Ket`](@ref)または[`Operator`](@ref)である必要があります。
