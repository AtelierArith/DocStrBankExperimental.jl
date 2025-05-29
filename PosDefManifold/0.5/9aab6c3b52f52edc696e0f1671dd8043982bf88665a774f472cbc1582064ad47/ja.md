```
mean(metric::Metric, ν::Vector{T}) where T<:RealOrComplex
```

指定された `metric` の型 [Metric::Enumerated type](@ref) を使用して、$k$ 個の実数または複素数スカラーの平均を計算します。Fisher、logEuclidean、およびJeffreyメトリックを使用する場合、結果として得られる平均はスカラー幾何平均であることに注意してください。また、このメソッドのコードはユニット *statistics.jl* にあり、他のすべてのコードはユニット *riemannianGeometry.jl* にあります。

**例**

```julia
using PosDefManifold
# 自由度2のカイ二乗分布に従う10個のランダムな数を生成します。
ν=[randχ²(2) for i=1:10]
arithmetic_mean=mean(Euclidean, ν)
geometric_mean=mean(Fisher, ν)
harmonic_mean=mean(invEuclidean, ν)
harmonic_mean<=geometric_mean<=arithmetic_mean # AGH不等式
```
