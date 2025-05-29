```julia
function statistic(x::IntVec, y::UniData, stat::AnovaF_IS; 
                k::Into=nothing, 
                ns::Union{Vector{Int}, Nothing}=nothing, 
                kwargs...) 
```

1-way ANOVAの*F*統計量は独立したサンプルのためのもので、[Edgington (1995)](@ref "References")の60ページを参照してください。

データはユニークなベクトル`y`として与えられ、各グループの観測値を自然な順序で保持します。したがって、$K$グループの場合、`y`は$N=N_1+ \ldots +N_K$要素を保持し、ここで$N_k$は$k^{th}$グループの観測数です。

`x`は[`membership(::IndSampStatistic)`](@ref)ベクトルです。

`k`はグループの数（独立したサンプル）です。省略すると計算されます。

`ns`は形式`ns=[N1,..., NK]`のグループの数のベクトルです。省略すると計算されます。

*例*

```julia
using PermutationTests
g1=[1.0, 2.0, 3.0, 4.0] # グループ1の観測値 
g2=[1.1, 2.8, 3.2, 4.4, 5.3] # グループ2の観測値 
ns=[length(g1), length(g2)] # N1, N2
y=vcat(g1, g2)
x=membership(AnovaF_IS(), ns)
F=statistic(x, y, AnovaF_IS())
# または、yからkとnsを見つけるのを避けるために
F2=statistic(x, y, AnovaF_IS(); k=2, ns=ns)

# 独立したサンプルのための双方向テストのt検定統計量の二乗は
# 上記のF検定統計量に等しい

t=statistic(x, y, StudentT_IS(); ns=ns)
println(t^2≈F ? "OK" : "error")

```
