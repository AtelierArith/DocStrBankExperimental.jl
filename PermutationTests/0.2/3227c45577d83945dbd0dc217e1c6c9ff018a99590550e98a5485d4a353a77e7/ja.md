```julia
function statistic(x::UniData, y::UniData, stat::CrossProd; 
                kwargs...)
```

データ入力ベクトル x と y のクロスプロダクト（内積）。

方向相関テストのためのピアソン相関 *r* テスト統計量に相当し、データが標準化されている場合は常に、[Statistic](@ref) を参照してください。

*例*

```julia
using PermutationTests
x, y = randn(10), randn(10)
c = statistic(x, y, CrossProd())
```
