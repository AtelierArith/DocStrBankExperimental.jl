```
StringCorrelator(d::Int; address=nothing, type=nothing) <: AbstractOperator{T}
```

1次元ハバード格子上の格子サイト間の文字相関を距離 `d` で抽出するための演算子で、`0 ≤ d < M` です。

$$
    Ĉ_{\text{string}}(d) = \frac{1}{M} \sum_{j}^{M} δ n̂_j
                                         (e^{i π \sum_{j ≤ k < j + d} δ n̂_k}) δ n̂_{j+d}
$$

ここで、$δ n̂_j = n̂_j - n̄$ は平均充填数からのボソン数の偏差であり、$n̄ = N/M$ は $N$ 粒子と $M$ 格子サイト（またはモード）の平均充填数です。

周期境界条件を持つ1次元格子を仮定します。使用法については [`SuperfluidCorrelator`](@ref) と [`AllOverlaps`](@ref) を参照してください。

デフォルトの要素型 `T` は `ComplexF64` です。これは `type` キーワード引数で上書きできます。`address` が提供されると、`T` はアドレス型から計算されます。非整数充填数の場合は `ComplexF64` に設定され、整数充填数または `d==0` の場合は `Float64` に設定されます。

さらに [`HubbardReal1D`](@ref)、[`G2RealCorrelator`](@ref)、[`SuperfluidCorrelator`](@ref)、[`AbstractOperator`](@ref)、および [`AllOverlaps`](@ref) を参照してください。
