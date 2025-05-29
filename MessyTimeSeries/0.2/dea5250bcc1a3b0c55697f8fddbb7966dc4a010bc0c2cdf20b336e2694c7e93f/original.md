```
forward_backwards_rw_interpolation(X::JMatrix{Float64})
```

Interpolate each non-stationary series in `X`, in turn, using a random walk logic both forward and backwards in time.

# Arguments

  * `X`: observed measurements (`nxT`)
