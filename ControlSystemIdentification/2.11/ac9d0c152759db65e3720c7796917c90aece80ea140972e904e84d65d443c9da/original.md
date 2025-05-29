```
tfest(data::FRD, basis::AbstractStateSpace; 
    freq_weight = 1 ./ (data.w .+ data.w[2]),
    opt = BFGS(),
    metric::M = abs2,
    opts = Optim.Options(
        store_trace       = true,
        show_trace        = true,
        show_every        = 50,
        iterations        = 1000000,
        allow_f_increases = false,
        time_limit        = 100,
        x_tol             = 1e-5,
        f_tol             = 0,
        g_tol             = 1e-8,
        f_calls_limit     = 0,
        g_calls_limit     = 0,
)
```

Fit a parametric transfer function to frequency-domain data using a pre-specified basis.

# Arguments:

  * `data`: An `FRD` onbject with frequency domain data.

function kautz(a::AbstractVector)

  * `basis`: A basis for the estimation. See, e.g., `laguerre, laguerre_oo, kautz`
  * `freq_weight`: A vector of weights per frequency. The default is approximately `1/f`.
  * `opt`: The Optim optimizer to use.
  * `opts`: `Optim.Options` controlling the solver options.
