```
precision(m::UBCM)
```

Determine the compute precision of the UBCM model `m`.

# Examples

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> MaxEntropyGraphs.precision(model)
Float64
```

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate), precision=Float32);

julia> MaxEntropyGraphs.precision(model)
Float32
```
