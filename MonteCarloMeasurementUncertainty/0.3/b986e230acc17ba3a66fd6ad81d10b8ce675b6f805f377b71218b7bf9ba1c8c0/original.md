```
push!(meas::TimeSeries, single_value::Number)
```

`push!` a single numerical value into the datastream. If the current datastream is full, meaning `length(meas.datastream) == meas.current_index`, then the datastream is `resize!`d when the value is pushed. Can result in `O(n)` complexity.
