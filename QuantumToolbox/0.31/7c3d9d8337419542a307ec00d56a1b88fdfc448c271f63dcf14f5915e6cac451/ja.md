```
hilbert_dist(ρ::QuantumObject, σ::QuantumObject)
```

2つの [`QuantumObject`](@ref) の間のヒルベルト-シュミット距離を計算します: $D_{HS}(\hat{\rho}, \hat{\sigma}) = \textrm{Tr}\left[\hat{A}^\dagger \hat{A}\right]$、ここで $\hat{A} = \hat{\rho} - \hat{\sigma}$ です。

`ρ` と `σ` は、[`Ket`](@ref) または [`Operator`](@ref) のいずれかである必要があります。

# 参考文献

  * [Vedral-Plenio1998](@citet)
