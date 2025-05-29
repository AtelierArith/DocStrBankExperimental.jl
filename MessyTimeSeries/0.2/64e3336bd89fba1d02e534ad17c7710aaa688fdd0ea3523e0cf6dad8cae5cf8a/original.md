```
interpolate_series(X::JMatrix{Float64}, n::Int64, T::Int64)
```

Interpolate each series in `X`, in turn, by replacing missing observations with the sample average of the non-missing values.

# Arguments

  * `X`: observed measurements (`nxT`)
  * `n` and `T` are the number of series and observations
