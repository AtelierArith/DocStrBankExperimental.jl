```
InterpenetratedTopologyResult <: AbstractVector{Tuple{TopologyResult,Int}}
```

The result of a topology computation on a structure containing possibly several interpenetrated substructures.

An `InterpenetratedTopologyResult` can be seen as a list of `(topology, n)` pair where

  * `topology` is the [`TopologyResult`](@ref) corresponding to the substructures.
  * `n` is an integer such that the substructure is composed of an `n`-fold catenated net.

The entire structure can thus be decomposed in a series of substructures, each of them possibly decomposed into several catenated nets.

!!! info "Vocabulary"
    In this context, *interpenetration* and *catenation* have slightly different meanings:

      * two (or more) substructures are *interpenetrated* if both are present in the unit cell, and are composed of vertices that have disjoint numbers. They may or may not all have the same topology since they are disjoint and independent subgraphs. For example:

        ```jldoctest
        julia> topological_genome(PeriodicGraph("2   1 1  0 1   2 2  0 1   2 2  1 0"))
        2 interpenetrated substructures:
        ⋅ Subnet 1 → UNKNOWN 1 1 1 1
        ⋅ Subnet 2 → sql
        ```
      * a net is `n`-fold *catenated* if the unit cell of a single connected component of the net is `n` times larger than the unit cell of the overall net. In that case, the net is actually made of `n` interpenetrating connected components, which all have the same topology. For example:

        ```jldoctest
        julia> topological_genome(PeriodicGraph("3   1 1  2 0 0   1 1  0 1 0   1 1  0 0 1"))
        (2-fold) pcu
        ```

    Both may occur inside a single structure, for example:

    ```jldoctest
    julia> topological_genome(PeriodicGraph("2   1 1  0 2   2 2  0 1   2 2  1 0"))
    2 interpenetrated substructures:
    ⋅ Subnet 1 → (2-fold) UNKNOWN 1 1 1 1
    ⋅ Subnet 2 → sql
    ```

    Note that catenation is a particular case of interpenetration: an `n`-fold catenated net repeated into a supercell `n` times larger becomes `n` interpenetrated nets.

    !!! tip
        See also [`total_interpenetration`](@ref) to abstract away the difference between interpenetration and catenation.


# Example

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

julia> topology, n = topologies[2]; # second subnet

julia> n # catenation multiplicity
1

julia> topology
AllNodes, SingleNodes, Standard: pto
PE: sqc11259

julia> typeof(topology)
TopologyResult
```
