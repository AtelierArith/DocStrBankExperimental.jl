```
product_distribution(dists::AbstractArray{<:Distribution{<:ArrayLikeVariate{M}},N})
```

独立した `M` 次元分布の積分布として、`M + N` 次元配列の分布を作成します。

この関数は、[`ProductDistribution`](@ref) 分布を構築することにフォールバックしますが、特化したメソッドを定義することもできます。
