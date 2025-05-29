```
isproper([ space = NaturalParametersSpace() ], ::Type{T}, parameters, conditioner = nothing) where { T <: Distribution }
```

`isproper`の特定のバージョンで、`Distributions.jl`パッケージの分布タイプに特に定義されています。`ExponentialFamilyDistribution`のインスタンスを必要とせず、特定の分布タイプで直接呼び出すことができます。オプションで、パラメータ空間を定義する`space`パラメータを受け入れます。条件付き指数族分布には、追加の`conditioner`引数が必要です。

参照: [`NaturalParametersSpace`](@ref), [`MeanParametersSpace`](@ref)
