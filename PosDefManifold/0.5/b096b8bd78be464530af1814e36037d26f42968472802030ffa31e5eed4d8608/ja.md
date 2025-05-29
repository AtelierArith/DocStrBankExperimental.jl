```
std(metric::Metric, ν::Vector{T};
    corrected::Bool=true,
    mean=nothing) where T<:RealOrComplex
```

指定された `metric` のタイプ [Metric::Enumerated type](@ref) と、提供された場合は指定された `mean` を使用して、$k$ 個の実数または複素数スカラーの標準偏差を計算します。

この関数ではユークリッド距離とフィッシャー距離のみがサポートされています。ユークリッド距離を使用すると、標準のJulia [std](https://docs.julialang.org/en/v1/stdlib/Statistics/#Statistics.std) 関数の出力が返されます。フィッシャー距離を使用すると、スカラー幾何学的標準偏差が返され、これは次のように定義されます。

$$
\sigma=\text{exp}\Big(\sqrt{k^{-1}\sum_{i=1}^{k}\text{ln}^2(v_i/\mu})\Big)
$$

。

`corrected` が `true` の場合、合計は $k-1$ でスケーリングされますが、`false` の場合は合計は $k$ でスケーリングされます。

**例**

```julia
using PosDefManifold
# 自由度2のカイ二乗分布に従う10個のランダムな数を生成します。
ν=[randχ²(2) for i=1:10]
arithmetic_sd=std(Euclidean, ν) # 平均は提供されていません
geometric_mean=mean(Fisher, ν)
geometric_sd=std(Fisher, ν, mean=geometric_mean) # 平均が提供されています
```
