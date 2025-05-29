```
TopologyResult
```

The result of a topology computation on a structure with different [`Clustering`](@ref) options.

Its representation includes the name of the clustering options along with their corresponding genome. It is omitted if there is only one clustering option which is [`Auto`](@ref Clustering).

Like for a [`TopologicalGenome`](@ref) (or a `PeriodicGraph`), the textual representation of a `TopologyResult` can be parsed back to a `TopologyResult`:

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

See also [`TopologicalGenome`](@ref) and [`InterpenetratedTopologyResult`](@ref).
