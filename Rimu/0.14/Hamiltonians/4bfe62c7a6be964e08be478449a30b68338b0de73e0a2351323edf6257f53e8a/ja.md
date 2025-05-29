```
G2RealCorrelator(d::Int) <: AbstractOperator{Float64}
```

サイト間の密度-密度相関のための二体演算子で、`0 ≤ d < M` の範囲で `d` によって分離されています。

$$
    \hat{G}^{(2)}(d) = \frac{1}{M} \sum_i^M \hat{n}_i (\hat{n}_{i+d} - \delta_{0d}).
$$

周期境界条件を持つ一次元格子を仮定し、

$$
    \hat{G}^{(2)}(-M/2 \leq d < 0) = \hat{G}^{(2)}(|d|),
$$

$$
    \hat{G}^{(2)}(M/2 < d < M) = \hat{G}^{(2)}(M - d),
$$

および正規化

$$
    \sum_{d=0}^{M-1} \langle \hat{G}^{(2)}(d) \rangle = \frac{N (N-1)}{M}.
$$

多成分基底の場合、すべての粒子間の相関を均等に計算し、すべての成分を単一のフォック状態にスタッキングすることに相当します。

# 引数

  * `d::Integer`: サイト間の距離。

# 参照

  * [`HubbardReal1D`](@ref)
  * [`G2RealSpace`](@ref)
  * [`G2MomCorrelator`](@ref)
  * [`AbstractOperator`](@ref)
  * [`AllOverlaps`](@ref)
