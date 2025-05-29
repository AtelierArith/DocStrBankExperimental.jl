```
fidelity(ρ::QuantumObject, σ::QuantumObject)
```

2つの[`QuantumObject`](@ref)の忠実度を計算します: $F(\hat{\rho}, \hat{\sigma}) = \textrm{Tr} \sqrt{\sqrt{\hat{\rho}} \hat{\sigma} \sqrt{\hat{\rho}}}$

ここで、定義は[Nielsen-Chuang2011](@citet)からのものです。これは[Jozsa1994](@citet)で定義された忠実度の平方根です。

`ρ`と`σ`は、[`Ket`](@ref)または[`Operator`](@ref)でなければなりません。
