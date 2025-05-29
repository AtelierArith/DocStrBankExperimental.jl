```
entropy_relative(ρ::QuantumObject, σ::QuantumObject; base::Int=0, tol::Real=1e-15)
```

$$
\hat{\rho}
$$

に対する$\hat{\sigma}$の[量子相対エントロピー](https://en.wikipedia.org/wiki/Quantum_relative_entropy)を計算します: $D(\hat{\rho}||\hat{\sigma}) = \textrm{Tr} \left[ \hat{\rho} \log \left( \hat{\rho} \right) \right] - \textrm{Tr} \left[ \hat{\rho} \log \left( \hat{\sigma} \right) \right]$。

# 注意事項

  * `ρ`は量子状態であり、[`Ket`](@ref)または[`Operator`](@ref)のいずれかです。
  * `σ`は量子状態であり、[`Ket`](@ref)または[`Operator`](@ref)のいずれかです。
  * `base`は使用する対数の底を指定し、デフォルト値`0`を使用する場合は自然対数が使用されます。
  * `tol`は密度行列$\hat{\rho}$のゼロ値の固有値を検出するための絶対許容誤差を示します。

# 参考文献

  * [Nielsen-Chuang2011; section 11.3.1, page 511](@citet)
