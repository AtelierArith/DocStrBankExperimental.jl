```
dbaclust(
    sequences,
    nclust::Int,
    dtwdist::DTWDistance;
    n_init::Int           = 1,
    iterations::Int       = 100,
    inner_iterations::Int = 10,
    rtol::Float64         = 1e-4,
    rtol_inner::Float64   = rtol,
    threaded::Bool        = false,
    show_progress::Bool   = true,
    store_trace::Bool     = true,
    i2min::AbstractVector = [],
    i2max::AbstractVector = [],
)
```

# Arguments:

  * `nclust`: Number of clsuters
  * `n_init`: Number of initialization tries
  * `inner_iterations`: Number of iterations in the inner alg.
  * `i2min`: Bounds on the warping path
  * `threaded`: Use multi-threading
