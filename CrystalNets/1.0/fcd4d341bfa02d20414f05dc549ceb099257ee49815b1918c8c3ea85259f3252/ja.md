```
InterpenetratedTopologyResult <: AbstractVector{Tuple{TopologyResult,Int}}
```

構造体内の複数の相互貫通するサブ構造を含むトポロジー計算の結果。

`InterpenetratedTopologyResult` は、`(topology, n)` のペアのリストとして見ることができ、ここで

  * `topology` はサブ構造に対応する [`TopologyResult`](@ref) です。
  * `n` は整数で、サブ構造が `n` 倍のカテネートネットで構成されていることを示します。

したがって、全体の構造は一連のサブ構造に分解でき、それぞれが複数のカテネートネットに分解される可能性があります。

!!! info "語彙"
    この文脈において、*相互貫通* と *カテネーション* は若干異なる意味を持ちます：

      * 二つ（またはそれ以上）のサブ構造は、両方が単位セルに存在し、互いに異なる番号を持つ頂点で構成されている場合に *相互貫通* しています。これらは互いに異なる独立したサブグラフであるため、必ずしも同じトポロジーを持つわけではありません。例えば：

        ```jldoctest
        julia> topological_genome(PeriodicGraph("2   1 1  0 1   2 2  0 1   2 2  1 0"))
        2 interpenetrated substructures:
        ⋅ Subnet 1 → UNKNOWN 1 1 1 1
        ⋅ Subnet 2 → sql
        ```
      * ネットは、ネットの単一の連結成分の単位セルが全体のネットの単位セルの `n` 倍大きい場合に `n` 倍 *カテネート* されています。この場合、ネットは実際には `n` 個の相互貫通する連結成分で構成されており、すべて同じトポロジーを持っています。例えば：

        ```jldoctest
        julia> topological_genome(PeriodicGraph("3   1 1  2 0 0   1 1  0 1 0   1 1  0 0 1"))
        (2-fold) pcu
        ```

    両方が単一の構造内で発生する可能性があります。例えば：

    ```jldoctest
    julia> topological_genome(PeriodicGraph("2   1 1  0 2   2 2  0 1   2 2  1 0"))
    2 interpenetrated substructures:
    ⋅ Subnet 1 → (2-fold) UNKNOWN 1 1 1 1
    ⋅ Subnet 2 → sql
    ```

    カテネーションは相互貫通の特別なケースであることに注意してください：`n` 倍カテネートされたネットが `n` 倍大きなスーパーセルに繰り返されると、`n` 個の相互貫通するネットになります。

    !!! tip
        相互貫通とカテネーションの違いを抽象化するために、[`total_interpenetration`](@ref) も参照してください。


# 例

```jldoctest
julia> mof14 = joinpath(dirname(dirname(pathof(CrystalNets))), "test", "cif", "MOFs", "MOF-14.cif");

julia> topologies = determine_topology(mof14, structure=StructureType.MOF, clusterings=[Clustering.Auto, Clustering.Standard, Clustering.PE])
2 interpenetrated substructures:
⋅ Subnet 1 → AllNodes,SingleNodes,Standard: pto | PE: sqc11259
⋅ Subnet 2 → AllNodes,SingleNodes,Standard: pto | PE: sqc11259

julia> typeof(topologies)
InterpenetratedTopologyResult

julia> parse(InterpenetratedTopologyResult, repr(topologies)) == topologies
true

julia> topologies[2]
(AllNodes, SingleNodes, Standard: pto
PE: sqc11259, 1)

julia> topology, n = topologies[2]; # 第二のサブネット

julia> n # カテネーションの重複度
1

julia> topology
AllNodes, SingleNodes, Standard: pto
PE: sqc11259

julia> typeof(topology)
TopologyResult
```
