```
measure_data(mref::MeasureRef)::AbstractMeasureData
```

`mref`に関連付けられた測定データを返します。

**例**

```julia-repl
julia> data = measure_data(meas);

julia> typeof(data)
FunctionalDiscreteMeasureData{Vector{GeneralVariableRef},Vector{Float64}}
```
