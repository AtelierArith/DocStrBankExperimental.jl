```
hellinger_dist(ρ::QuantumObject, σ::QuantumObject)
```

2つの[`QuantumObject`](@ref)間の[ヘリンガー距離](https://en.wikipedia.org/wiki/Hellinger_distance)を計算します: $D_H(\hat{\rho}, \hat{\sigma}) = \sqrt{2 - 2 \textrm{Tr}\left(\sqrt{\hat{\rho}}\sqrt{\hat{\sigma}}\right)}$

`ρ`と`σ`は、[`Ket`](@ref)または[`Operator`](@ref)でなければなりません。

# 参考文献

  * [Spehner2017](@citet)
