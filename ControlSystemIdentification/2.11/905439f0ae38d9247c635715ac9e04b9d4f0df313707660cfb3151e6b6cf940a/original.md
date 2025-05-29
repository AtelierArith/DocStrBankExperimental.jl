```
tfest(
    data::FRD,
    p0,
    link = log ∘ abs;
    freq_weight = sqrt(data.w[1]*data.w[end]),
    refine = true,
    opt = BFGS(),
    opts = Optim.Options(
        store_trace       = true,
        show_trace        = true,
        show_every        = 1,
        iterations        = 100,
        allow_f_increases = false,
        time_limit        = 100,
        x_tol             = 0,
        f_tol             = 0,
        g_tol             = 1e-8,
        f_calls_limit     = 0,
        g_calls_limit     = 0,
    ),
)
```

Fit a parametric transfer function to frequency-domain data.

The initial pahse of the optimization solves

$$
\operatorname{minimize}_{B,A}{|| B/l - A||}
$$

and the second stage (if refine=true) solves 

$$
\operatorname{minimize}_{B,A}{|| \text{link}\left(\dfrac{B}{A}\right) - \text{link}\left(l\right)||}
$$

(`abs2(link(B/A) - link(l))`)

# Arguments:

  * `data`: An `FRD` onbject with frequency domain data.
  * `p0`: Initial parameter guess. Can be a `NamedTuple` or `ComponentVector` with fields `b,a` specifying numerator and denominator as they appear in the call to `tf`, i.e., `(b = [1.0], a = [1.0,1.0,1.0])`. Can also be an instace of `TransferFunction`.
  * `link`: By default, phase information is discarded in the fitting. To include phase, change to `link = log`.
  * `freq_weight`: Apply weighting with the inverse frequency. The value determines the cutoff frequency before which the weight is constant, after which the weight decreases linearly. Defaults to the geometric mean of the smallest and largest frequency.
  * `refine`: Indicate whether or not a second optimization stage is performed to refine the results of the first.
  * `opt`: The Optim optimizer to use.
  * `opts`: `Optim.Options` controlling the solver options.

See also [`minimum_phase`](@ref) to transform a possibly non-minimum phase system to minimum phase.
