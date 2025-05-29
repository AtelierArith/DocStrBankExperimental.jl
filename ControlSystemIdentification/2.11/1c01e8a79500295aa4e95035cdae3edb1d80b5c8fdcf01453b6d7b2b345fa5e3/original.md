```
era(d::AbstractIdData, nx; m = 2nx, n = 2nx, l = 5nx, p = l, λ=0, smooth=false)
era(ds::Vector{IdData}, nx; m = 2nx, n = 2nx, l = 5nx, p = l, λ=0, smooth=false)
```

Eigenvalue realization algorithm. Uses [`okid`](@ref) to find the Markov parameters as an initial step.

The parameter `l` is likely to require tuning, a reasonable starting point to choose `l` large enough for the impulse response to have mostly dissipated.

If a vector of datasets is provided, the Markov parameters estimated from each experiment are averaged before calling `era`. This allows use of data from multiple experiments to improve the model estimate.

# Arguments:

  * `nx`: Model order
  * `l`: Number of Markov parameters to estimate.
  * `λ`: Regularization parameter (don't overuse this, prefer to make more experiments instead)
  * `smooth`: If true, the regularization given by `λ` penalizes curvature in the estimated impulse response.
  * `p`: Optionally, delete the first `p` columns in the internal Hankel matrices to account for initial conditions != 0. If `x0 != 0`, for `era`, `p` defaults to `l`, while when calling [`okid`](@ref) directly, `p` defaults to 0.
