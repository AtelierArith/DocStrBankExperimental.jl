```
bures_dist(ρ::QuantumObject, σ::QuantumObject)
```

2つの[`QuantumObject`](@ref)間の[Bures距離](https://en.wikipedia.org/wiki/Bures_metric)を計算します: $D_B(\hat{\rho}, \hat{\sigma}) = \sqrt{2 \left(1 - F(\hat{\rho}, \hat{\sigma}) \right)}$

ここで、[`fidelity`](@ref) $F$の定義は[Nielsen-Chuang2011](@citet)からのものです。これは[Jozsa1994](@citet)で定義されたフィデリティの平方根です。

`ρ`と`σ`は、[`Ket`](@ref)または[`Operator`](@ref)でなければなりません。
