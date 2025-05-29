```julia
function statistic(x::Tuple, y::UniData, stat::StudentT_1S; 
                ∑y²::Realo=nothing, 
                kwargs...) 
```

スチューデントの一標本 *t* 統計量。

`y` は入力データです。

`x` は `y` の要素数と同じ数の 1.0 を持つタプルです。

`∑y²` は計算を高速化するためにオプションで提供できます。この量はデータの順列によって不変です。エクスポートされた関数 `_∑y²` をこの目的で使用できます。以下の例を参照してください。

*例*

```julia
using PermutationsTest
y=randn(6);
x=(1., 1., 1., 1., 1., 1.);
t=statistic(x, y, StudentT_1S()) 

pcd=_∑y²(y)
t2=statistic(x, y, StudentT_1S(); ∑y²=pcd) 
println(t≈t2 ? "OK" : "Error")
```
