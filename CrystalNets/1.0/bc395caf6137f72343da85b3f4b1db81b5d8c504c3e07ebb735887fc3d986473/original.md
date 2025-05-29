```
const REVERSE_CRYSTALNETS_ARCHIVE::Dict{String,String}
```

Reverse of [`CRYSTALNETS_ARCHIVE`](@ref).

Can be used to query the topological genome of known nets, as in:

```jldoctest
julia> REVERSE_CRYSTALNETS_ARCHIVE["dia"]
"3 1 2 0 0 0 1 2 0 0 1 1 2 0 1 0 1 2 1 0 0"

julia> topological_genome(CrystalNet(PeriodicGraph(ans)))
dia
```

!!! note
    It is also possible to directly access the topological genome as a `PeriodicGraph` by parsing the name as a [`TopologicalGenome`](@ref):

    ```jldoctest
    julia> PeriodicGraph(parse(TopologicalGenome, "pcu"))
    PeriodicGraph3D(1, PeriodicEdge3D[(1, 1, (0,0,1)), (1, 1, (0,1,0)), (1, 1, (1,0,0))])

    julia> string(PeriodicGraph(parse(TopologicalGenome, "nbo"))) == REVERSE_CRYSTALNETS_ARCHIVE["nbo"]
    true
    ```

