```
Base.run(mi::ModelInstance, ntimesteps::Int=typemax(Int),
        dimkeys::Union{Nothing, Dict{Symbol, Vector{T} where T <: DimensionKeyTypes}}=nothing)
```

Run the `ModelInstance` `mi` once with `ntimesteps` and dimension keys `dimkeys`.
