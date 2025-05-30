```
TopologyResult
```

異なる [`Clustering`](@ref) オプションを持つ構造に対するトポロジー計算の結果です。

その表現には、クラスタリングオプションの名前とそれに対応するゲノムが含まれます。クラスタリングオプションが一つだけである場合は、[`Auto`](@ref Clustering) は省略されます。

[`TopologicalGenome`](@ref) （または `PeriodicGraph`）と同様に、`TopologyResult` のテキスト表現は `TopologyResult` に再解析できます：

```jldoctest
julia> mof5 = joinpath(dirname(dirname(pathof(CrystalNets))), "test", "cif", "MOF-5.cif");

julia> topologies = only(determine_topology(mof5, structure=StructureType.MOF, clusterings=[Clustering.Auto, Clustering.Standard, Clustering.PE]))[1]
AllNodes, SingleNodes: pcu
Standard: xbh
PE: cab

julia> typeof(topologies)
TopologyResult

julia> parse(TopologyResult, repr(topologies)) == topologies
true
```

[`TopologicalGenome`](@ref) および [`InterpenetratedTopologyResult`](@ref) も参照してください。
