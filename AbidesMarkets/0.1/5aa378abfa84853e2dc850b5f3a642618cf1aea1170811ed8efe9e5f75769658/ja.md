```
aggregate_LOB_measurement_eop(X::Union{Vector{Float64}, JVector{Float64}}, times::Vector{Time}, time_step::Period)
```

指定された `time_step` で取得された EOP 測定値を返すことによって `X` を集約します。
