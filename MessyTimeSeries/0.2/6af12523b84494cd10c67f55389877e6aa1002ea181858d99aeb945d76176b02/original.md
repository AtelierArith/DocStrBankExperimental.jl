```
centred_moving_average(X::Union{FloatMatrix, JMatrix{Float64}}, window::Int64)
```

Compute the centred moving average of `X`.

# Arguments

  * `X`: observed measurements (`nxT`)
  * `window` is the total number of observations (lagging, current and leading) included in the average
