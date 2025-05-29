```
measurement(::MonteCarloMeasurement)
```

[`measurement`](https://github.com/JuliaPhysics/Measurements.jl/blob/5e84abee8ca66205d21cd654e9a2d7aa6fab9923/src/Measurements.jl#L106-L119) は [`Measurements.jl`](https://github.com/JuliaPhysics/Measurements.jl) からの [`MonteCarloMeasurement`](@ref) に対してディスパッチされます。 これは、引数に格納されたデータストリームに対して [`binning_analysis`](@ref) を呼び出します。

```jldoctest measurement_example
julia> acc = AccumulatedSeries("Measurement Test");

julia> for idx ∈ 1:Int(2^18) push!(acc, idx % 512) end;

julia> measurement(acc)
260.0 ± 150.0
```
