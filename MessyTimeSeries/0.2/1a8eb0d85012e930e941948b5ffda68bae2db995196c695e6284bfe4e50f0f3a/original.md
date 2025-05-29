```
lag(X::FloatArray, p::Int64)
```

Construct the data required to run a standard vector autoregression.

# Arguments

  * `X`: observed measurements (`nxT`), where `n` and `T` are the number of series and observations.
  * `p`: number of lags in the vector autoregression

# Output

  * `X_{t}`
  * `X_{t-1}`
