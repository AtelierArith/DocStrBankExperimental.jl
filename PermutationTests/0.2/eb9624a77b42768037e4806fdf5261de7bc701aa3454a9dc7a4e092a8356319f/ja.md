```julia
function statistic(x::IntVec, y::UniData, stat::AnovaF_RM; 
                ns::@NamedTuple{n::Int, k::Int}, 
                ∑Y²kn::Realo=nothing, 
                ∑y²::Realo=nothing, 
                ∑S²k::Realo=nothing, 
                kwargs...) 
```

1-way ANOVAの*F*統計量（反復測定用）、詳細は[Edgington (1995)](@ref "References")の102ページを参照してください。

データは、自然な順序で$K$の測定（処置、時間、...）に対する$N$の観察を連結したユニークなベクトル`y`として与えられます。つまり、観察1のための$K$の処置、...、観察$N$のための$K$の処置です。したがって、`y`は$N \cdot K$の要素を保持します。

`x`は[`membership(::RepMeasStatistic)`](@ref)ベクトルです。

`ns`は、形式が`(n=N, k=K)`のjuliaの[named tuple](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types)です（以下の例を参照）。

`∑Y²kn`、`∑y²`、および`∑S²k`は、データの順列によって不変であるため、計算を高速化するためにオプションで提供できます。この目的のためにエクスポートされた関数`_∑Y²kn_∑y²_∑S²k`を使用できます。以下の例を参照してください。

*例*

```julia
using PermutationTests
# K=2（測定）、N=4（観察）
o1=[1.0, 2.0]; # 最初の観察 
o2=[2.0, 2.8]; # 2番目の観察 
o3=[3.0, 2.6]; # 3番目の観察
o4=[4.0, 4.1]; # 4番目の観察
ns=(n=4, k=2); # 4つの観察と2つの測定
y=vcat(o1, o2, o3, o4);
x=membership(AnovaF_RM(), ns);
F=statistic(x, y, AnovaF_RM(); ns=ns)

# 一部のデータを事前計算
pcd=_∑Y²kn_∑y²_∑S²k(y, ns);
F2=statistic(x, y, AnovaF_RM(); ns=ns, ∑Y²kn=pcd[1], ∑y²=pcd[2], ∑S²k=pcd[3])

# 反復測定のt検定統計量は、2つの測定の差に対する1標本t検定統計量と同じです。
# 双方向検定のためのそれらの統計量の平方は、上記のF検定統計量に等しいです。

x=membership(StudentT_1S(), ns.n)
t=statistic(x, y[1:2:ns.n*2-1].-y[2:2:ns.n*2], StudentT_1S())
println(t^2≈F ? "OK" : "error")

```
