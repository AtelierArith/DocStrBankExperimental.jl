```
precision(m::BiCM)
```

Determine the compute precision of the BiCM model `m`.

# Examples

```jldoctest
julia> model = BiCM(corporateclub());

julia> MaxEntropyGraphs.precision(model)
Float64
```

```jldoctest
julia> model = BiCM(corporateclub(), precision=Float32);

julia> MaxEntropyGraphs.precision(model)
Float32
```
