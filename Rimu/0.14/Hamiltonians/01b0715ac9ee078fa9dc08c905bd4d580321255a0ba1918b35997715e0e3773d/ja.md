```
SuperfluidCorrelator(d::Int) <: AbstractOperator{Float64}
```

距離 `d` で離れたサイト間の超流動相関を抽出するための演算子で、`0 ≤ d < M` です：

$$
    \hat{C}_{\text{SF}}(d) = \frac{1}{M} \sum_{i}^{M} a_{i}^{\dagger} a_{i + d}
$$

$$
M
$$

サイトの一次元格子と周期境界条件を仮定します。$M$ はファック状態アドレスのモード数でもあります。

# 使用法

超流動相関は、`SuperfluidCorrelator` を [`AllOverlaps`](@ref) でラップし、`replica` キーワード引数を使って [`ProjectorMonteCarloProblem`](@ref) に渡すことで、モンテカルロ計算から抽出できます。 [`G2RealCorrelator`](@ref) の類似の使用例については、[G2 Correlator Example](https://RimuQMC.github.io/Rimu.jl/previews/PR227/generated/G2-example.html) を参照してください。

また、[`HubbardReal1D`](@ref)、[`G2RealCorrelator`](@ref)、[`AbstractOperator`](@ref)、および [`AllOverlaps`](@ref) も参照してください。
