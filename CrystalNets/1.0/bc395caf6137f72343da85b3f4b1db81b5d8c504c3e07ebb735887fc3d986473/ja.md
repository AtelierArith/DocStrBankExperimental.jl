```
const REVERSE_CRYSTALNETS_ARCHIVE::Dict{String,String}
```

[`CRYSTALNETS_ARCHIVE`](@ref) の逆です。

既知のネットのトポロジカルゲノムをクエリするために使用できます。例えば：

```jldoctest
julia> REVERSE_CRYSTALNETS_ARCHIVE["dia"]
"3 1 2 0 0 0 1 2 0 0 1 1 2 0 1 0 1 2 1 0 0"

julia> topological_genome(CrystalNet(PeriodicGraph(ans)))
dia
```

!!! note
    名前を [`TopologicalGenome`](@ref) として解析することで、`PeriodicGraph` としてトポロジカルゲノムに直接アクセスすることも可能です：

    ```jldoctest
    julia> PeriodicGraph(parse(TopologicalGenome, "pcu"))
    PeriodicGraph3D(1, PeriodicEdge3D[(1, 1, (0,0,1)), (1, 1, (0,1,0)), (1, 1, (1,0,0))])

    julia> string(PeriodicGraph(parse(TopologicalGenome, "nbo"))) == REVERSE_CRYSTALNETS_ARCHIVE["nbo"]
    true
    ```

