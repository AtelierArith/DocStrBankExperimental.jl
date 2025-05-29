```
bures_angle(ρ::QuantumObject, σ::QuantumObject)
```

2つの[`QuantumObject`](@ref)間の[Bures角](https://en.wikipedia.org/wiki/Bures_metric)を計算します: $D_A(\hat{\rho}, \hat{\sigma}) = \arccos\left(F(\hat{\rho}, \hat{\sigma})\right)$

ここで、[`fidelity`](@ref) $F$の定義は[Nielsen-Chuang2011](@citet)からのものです。これは[Jozsa1994](@citet)で定義されたフィデリティの平方根です。

`ρ`と`σ`は、[`Ket`](@ref)または[`Operator`](@ref)でなければなりません。
