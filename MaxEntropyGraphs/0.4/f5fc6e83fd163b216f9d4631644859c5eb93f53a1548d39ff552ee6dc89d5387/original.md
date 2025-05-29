```
precision(m::DBCM)
```

Determine the compute precision of the DBCM model `m`.

# Examples

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> MaxEntropyGraphs.precision(model)
Float64
```

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()), precision=Float32);

julia> MaxEntropyGraphs.precision(model)
Float32
```
