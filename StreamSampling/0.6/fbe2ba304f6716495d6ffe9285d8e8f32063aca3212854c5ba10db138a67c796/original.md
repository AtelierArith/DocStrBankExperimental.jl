```
ReservoirSample{T}([rng], method = AlgRSWRSKIP())
ReservoirSample{T}([rng], n::Int, method = AlgL(); ordered = false)
```

Initializes a reservoir sample which can then be fitted with [`fit!`](@ref). The first signature represents a sample where only a single element is collected. If `ordered` is true, the reservoir sample values can be retrived in the order they were collected with [`ordvalue`](@ref).

Look at the [`Sampling Algorithms`](@ref) section for the supported methods. 
