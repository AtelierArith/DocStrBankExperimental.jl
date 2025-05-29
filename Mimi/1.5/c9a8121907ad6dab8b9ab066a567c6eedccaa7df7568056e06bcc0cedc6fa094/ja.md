```
Base.run(mi::ModelInstance, ntimesteps::Int=typemax(Int),
        dimkeys::Union{Nothing, Dict{Symbol, Vector{T} where T <: DimensionKeyTypes}}=nothing)
```

`ModelInstance` `mi`を`ntimesteps`と次元キー`dimkeys`で1回実行します。
