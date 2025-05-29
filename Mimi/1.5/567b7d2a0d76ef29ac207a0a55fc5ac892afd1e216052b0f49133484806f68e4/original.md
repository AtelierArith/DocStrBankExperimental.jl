```
Base.run(m::Model; ntimesteps::Int=typemax(Int), rebuild::Bool=false,
        dim_keys::Union{Nothing, Dict{Symbol, Vector{T} where T <: DimensionKeyTypes}}=nothing)
```

Run model `m` once.
