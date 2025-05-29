```
measure_data(mref::MeasureRef)::AbstractMeasureData
```

Return the measure data associated with `mref`.

**Example**

```julia-repl
julia> data = measure_data(meas);

julia> typeof(data)
FunctionalDiscreteMeasureData{Vector{GeneralVariableRef},Vector{Float64}}
```
