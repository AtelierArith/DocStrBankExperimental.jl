```
H = okid(d::AbstractIdData, nx, l = 5nx; p = 1, λ=0, estimator = /)
```

Observer Kalman filter identification. Returns the Markov parameters (impulse response) `H` size `ny × nu × (l+1)`.

The parameter `l` is likely to require tuning, a reasonable starting point to choose `l` large enough for the impulse response to have mostly dissipated.

# Arguments:

  * `nx`: Model order
  * `l`: Number of Markov parameters to estimate (length of impulse response).
  * `λ`: Regularization parameter
  * `smooth`: If true, the regularization given by `λ` penalizes curvature in the estimated impulse response. If [`era`](@ref) is to be used after `okid`, favor a small `λ` with `smooth=true`, but if the impulse response is to be inspected by eye, a larger smoothing can yield a visually more accurate estimate of the impulse response.
  * `p`: Optionally, delete the first `p` columns in the internal Hankel matrices to account for initial conditions != 0. If `x0 != 0`, try setting `p` around the same value as `l`.
  * `estimator`: Function to use for estimating the Markov parameters. Defaults to `/` (least squares), but can also be a robust option such as `TotalLeastSquares.irls / flts` or `TotalLeastSquares.tls` for a total least-squares solutoins (errors in variables).
