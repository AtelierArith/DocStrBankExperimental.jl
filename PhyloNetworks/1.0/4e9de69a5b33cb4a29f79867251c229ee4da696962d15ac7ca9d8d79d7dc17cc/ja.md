```
hardwiredcluster(edge::Edge, taxa::Union{AbstractVector{String},AbstractVector{Int}})
hardwiredcluster!(v::Vector{Bool}, edge::Edge, taxa)
hardwiredcluster!(v::Vector{Bool}, edge::Edge, taxa, visited::Vector{Int})
```

`edge`のハードワイヤードクラスタを計算します。これは、エッジの子孫であるタクサに対してtrue、他のタクサ（欠損タクサを含む）に対してfalseのブール値のベクターとしてコーディングされます。

エッジは、`ischild1`が最新の状態である根付きネットワークに属している必要があります。事前に`directedges!`を実行してください。これは非常に重要です。そうしないと無限ループに入る可能性があり、関数はこれをテストしません。

visited: 訪問済みノードのすべてのノード番号のベクター。

# 例:

```jldoctest
julia> net5 = "(A,((B,#H1),(((C,(E)#H2),(#H2,F)),(D)#H1)));" |> readnewick |> directedges! ;

julia> taxa = net5 |> tiplabels # ABC EF D
6-element Vector{String}:
 "A"
 "B"
 "C"
 "E"
 "F"
 "D"

julia> hardwiredcluster(net5.edge[12], taxa) # 12番目のエッジの子孫 = CEF
6-element Vector{Bool}:
 0
 0
 1
 1
 1
 0
```

[`hardwiredclusterdistance`](@ref)および[`hardwiredclusters`](@ref)も参照してください。
