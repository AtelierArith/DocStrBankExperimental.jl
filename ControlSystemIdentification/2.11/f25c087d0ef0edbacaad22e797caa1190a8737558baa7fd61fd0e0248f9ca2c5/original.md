```
structured_pem(
    d,
    nx;
    focus = :prediction,
    p0,
    x0 = nothing,
    K0 = focus == :prediction ? zeros(nx, d.ny) : zeros(0,0),
    constructor,
    h = 1,
    metric::F = abs2,
    regularizer::RE = (p, P, simresult) -> 0,
    optimizer = BFGS(
        # alphaguess = LineSearches.InitialStatic(alpha = 0.95),
        linesearch = LineSearches.BackTracking(),
    ),
    store_trace = true,
    show_trace = true,
    show_every = 50,
    iterations = 10000,
    allow_f_increases = false,
    time_limit = 100,
    x_tol = 0,
    f_abstol = 1e-16,
    g_tol = 1e-12,
    f_calls_limit = 0,
    g_calls_limit = 0,
)
```

Linear gray-box model identification using the prediction-error method (PEM).

This function differs from [`newpem`](@ref) in that here, the user controls the structure of the estimated model, while in `newpem` a generic black-box structure is used.

The user provides the function `constructor(p)` that constructs the model from the parameter vector `p`. This function must return a statespace system. `p0` is the corresponding initial guess for the parameters. `K0` is an initial guess for the observer gain (only used if `focus = :prediciton`) and `x0` is the initial guess for the initial condition (estimated automatically if not provided).

For other options, see [`newpem`](@ref).
