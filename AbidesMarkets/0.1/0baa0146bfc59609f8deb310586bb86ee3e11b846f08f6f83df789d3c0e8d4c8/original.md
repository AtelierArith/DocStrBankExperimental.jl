```
compare_aggregated_LOB_measurements(X::JMatrix{Float64}, Y::JMatrix{Float64}, f_ticks::Function, f_time::Function)
```

Compare two vectors of aggregated LOB measurements. 

Each column of `X` and `Y` denotes a different point in time, while each row is a different entry (perhaps different levels).
