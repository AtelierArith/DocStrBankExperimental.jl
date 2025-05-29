```
InterpenetratedTopologyResult <: AbstractVector{Tuple{TopologyResult,Int}}
```

構造体に含まれる可能性のあるいくつかの相互貫通したサブ構造のトポロジー計算の結果。

`InterpenetratedTopologyResult`は、`(topology, n)`のペアのリストとして見ることができ、ここで

  * `topology`は、サブ構造に対応する[`TopologyResult`](@ref)です。
  * `n`は、サブ構造が`n`重に連結されたネットで構成されていることを示す整数です。

したがって、全体の構造は、一連のサブ構造に分解でき、それぞれがさらにいくつかの連結ネットに分解される可能性があります。

!!! info "語彙"
    この文脈において、*相互貫通*と*連結*はわずかに異なる意味を持ちます：

      * 2つ（またはそれ以上）のサブ構造が*相互貫通*しているのは、両方が単位セルに存在し、互いに異なる番号を持つ頂点で構成されている場合です。これらは、互いに異なる独立したサブグラフであるため、すべてが同じトポロジーを持つとは限りません。例えば：

        ```jldoctest
        julia> topological_genome(PeriodicGraph("2   1 1  0 1   2 2  0 1   2 2  1 0"))
        2つの相互貫通したサブ構造：
        ⋅ サブネット 1 → UNKNOWN 1 1 1 1
        ⋅ サブネット 2 → sql
        ```
      * ネットは、ネットの単一の連結成分の単位セルが全体のネットの単位セルの`n`倍大きい場合に`n`重*連結*されていると言います。この場合、ネットは実際には`n`個の相互貫通した連結成分で構成されており、すべてが同じトポロジーを持っています。例えば：

        ```jldoctest
        julia> topological_genome(PeriodicGraph("3   1 1  2 0 0   1 1  0 1 0   1 1  0 0 1"))
        (2重) pcu
        ```

    両方が単一の構造内で発生する可能性があります。例えば：

    ```jldoctest
    julia> topological_genome(PeriodicGraph("2   1 1  0 2   2 2  0 1   2 2  1 0"))
    2つの相互貫通したサブ構造：
    ⋅ サブネット 1 → (2重) UNKNOWN 1 1 1 1
    ⋅ サブネット 2 → sql
    ```

    連結は相互貫通の特別なケースであることに注意してください：`n`重に連結されたネットが`n`倍大きなスーパーセルに繰り返されると、`n`個の相互貫通したネットになります。

    !!! tip
        相互貫通と連結の違いを抽象化するために、[`total_interpenetration`](@ref)も参照してください。


# 例

```jldoctest
julia> mof14 = joinpath(dirname(dirname(pathof(CrystalNets))), "test", "cif", "MOFs", "MOF-14.cif");

julia> topologies = determine_topology(mof14, structure=StructureType.MOF, clusterings=[Clustering.Auto, Clustering.Standard, Clustering.PE])
2つの相互貫通したサブ構造：
⋅ サブネット 1 → AllNodes,SingleNodes,Standard: pto | PE: sqc11259
⋅ サブネット 2 → AllNodes,SingleNodes,Standard: pto | PE: sqc11259

julia> typeof(topologies)
InterpenetratedTopologyResult

julia> parse(InterpenetratedTopologyResult, repr(topologies)) == topologies
true

julia> topologies[2]
(AllNodes, SingleNodes, Standard: pto
PE: sqc11259, 1)

julia> topology, n = topologies[2]; # 2番目のサブネット

julia> n # 連結の重複度
1

julia> topology
AllNodes, SingleNodes, Standard: pto
PE: sqc11259

julia> typeof(topology)
TopologyResult
```
