```
measurement(::MonteCarloMeasurement)
```

Dispatch on [`measurement`](https://github.com/JuliaPhysics/Measurements.jl/blob/5e84abee8ca66205d21cd654e9a2d7aa6fab9923/src/Measurements.jl#L106-L119) from [`Measurements.jl`](https://github.com/JuliaPhysics/Measurements.jl) for a [`MonteCarloMeasurement`](@ref).  This will call a [`binning_analysis`](@ref) on the datastream stored in the argument.

```jldoctest measurement_example
julia> acc = AccumulatedSeries("Measurement Test");

julia> for idx ∈ 1:Int(2^18) push!(acc, idx % 512) end;

julia> measurement(acc)
260.0 ± 150.0
```
