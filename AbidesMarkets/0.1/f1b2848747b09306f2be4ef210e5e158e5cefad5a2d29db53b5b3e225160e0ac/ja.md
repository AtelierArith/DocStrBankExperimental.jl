```
aggregate_LOB_measurement_avg(X::Union{Vector{Float64}, JVector{Float64}}, times::Vector{Time}, time_step::Period)
```

指定された `time_step` で取得された平均（重複しない）測定値を返すことによって `X` を集約します。
