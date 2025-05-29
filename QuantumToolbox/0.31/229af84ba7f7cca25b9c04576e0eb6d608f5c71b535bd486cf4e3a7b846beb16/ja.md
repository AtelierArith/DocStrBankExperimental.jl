```
entropy_linear(ρ::QuantumObject)
```

量子線形エントロピー $S_L = 1 - \textrm{Tr} \left[ \hat{\rho}^2 \right]$ を計算します。ここで、$\hat{\rho}$ は系の密度行列です。

`ρ` は [`Ket`](@ref) または [`Operator`](@ref) のいずれかであることに注意してください。
