```julia
function statistic(x::UniData, y::UniData, stat::Covariance; 
                centered::Bool=false, 
                means::Tuple=(), 
                kwargs...)
```

データ入力ベクトル x と y の共分散。

双方向相関テストのためのピアソン相関 *r* テスト統計量に相当します。詳細は [Statistic](@ref) を参照してください。

オプションのキーワード引数については、メソッド [`statistic(x, y, stat::PearsonR)`](@ref) を参照してください。

*例*

```julia
using PermutationTests
x, y = randn(10), randn(10)
c1 = statistic(x, y, Covariance())

c2 = statistic(μ0(x), μ0(y), Covariance(); centered=true)

μx=μ(x)
μy=μ(y)
c3 = statistic(x, y, Covariance(); means=(μx, μy))
```

[`μ0`](@ref)、[`μ`](@ref) を参照してください。
