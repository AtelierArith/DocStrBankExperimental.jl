```
simulate(εs::AbstractArray, r::VectorAutoregression, Y0=nothing; kwargs...)
```

[`simulate!`](@ref) と同様ですが、結果のために `εs` のコピーを作成し、したがって `εs` を上書きしません。
