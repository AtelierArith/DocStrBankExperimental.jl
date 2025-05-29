```
interpolate_series(X::Union{FloatMatrix, JMatrix{Float64}})
```

Interpolate each series in `X`, in turn, by replacing missing observations with the sample average of the non-missing values.

# Arguments

  * `X`: observed measurements (`nxT`)
