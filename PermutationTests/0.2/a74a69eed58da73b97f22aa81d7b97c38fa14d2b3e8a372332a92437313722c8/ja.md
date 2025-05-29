```julia
function statistic(x::UniData, y::UniData, stat::StudentT_1S; 
                ∑y²::Realo=nothing, 
                kwargs...)
```

スチューデントの一標本 *t* 統計量。

`y` は入力データです。

`x` は [`membership(::OneSampStatistic)`](@ref) ベクトルです。

`∑y²` は計算を高速化するためにオプションで提供できます。この量はデータの順列によって不変です。エクスポートされた関数 `_∑y²` はこの目的のために使用できます。以下の例を参照してください。

*例*

```julia
using PermutationsTest
y=randn(6);
x=membership(StudentT_1S(), length(y));
t=statistic(x, y, StudentT_1S()) 

pcd=_∑y²(y)
t2=statistic(x, y, StudentT_1S(); ∑y²=pcd) 
println(t≈t2 ? "OK" : "Error")
```
