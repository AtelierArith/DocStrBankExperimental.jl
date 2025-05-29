```
simulate(εs::AbstractArray, var::VARProcess, Y0=nothing; nlag::Integer=arorder(var))
```

[`simulate!`](@ref) と同様ですが、結果のために `εs` のコピーを作成し、したがって `εs` を上書きしません。
