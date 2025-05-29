```
struct Network <: AbstractNetwork
    graph::MetaGraphsNext.AbstractGraph
    substation_bus::String
    Sbase::Real
    Vbase::Real
    Zbase::Real
    v0::Union{Real, AbstractVecOrMat{<:Number}}
    Ntimesteps::Int
    bounds::VariableBounds
    var_names::AbstractVector{Symbol}
end
```

`Network`モデルは、電力フローおよび最適電力フローモデルを作成するために必要なすべての入力を格納するために使用されます。Networkモデルの基盤には、ネットワーク内のエッジおよびノードデータを格納する`MetaGraphsNext.MetaGraph`があります。

私たちは、`AbstractNetwork`型を活用して、Networkモデルの直感的なインターフェースを作成します。たとえば、`edges(network)`は、バス名の値を持つエッジタプルのイテレータを返します（ただし、`Graphs.edges(MetaGraph)`を使用した場合、整数値を持つ`Graphs.SimpleGraphs.SimpleEdge`のイテレータが得られます）。

Networkは、`Dict`またはファイルパスを介して直接作成できます。最小限の入力には、[Conductor](@ref)仕様のベクターと、少なくとも`substation_bus`を含む`Network`キーが必要です。詳細については、[Input Formats](@ref)を参照してください。

`var_names`はデフォルトで空です。これは、`opf_results`のような結果取得者で使用されます。
