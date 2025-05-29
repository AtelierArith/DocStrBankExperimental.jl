```
(iter,resnorm)=opt_gauss_newton!(
    graph,
    objfun,
    discr;
    maxit = 100,
    logger = 0,
    errtype = :abserr,
    stoptol = 1e-6,
    cref = get_all_cref(graph),
    input = :A,
    γ0 = 1.0,
    linlsqr = :backslash,
    droptol = 0,
)
```

Applies the Gauss–Newton algorithm to solve the nonlinear least squares problem: Fit the output of the `graph` to the values of `objfun`, in the points `discr`.

The variable `graph` is modified during the iterations. The function returns the iteration `iter` where it terminated, and the corresponding residual norm `resnorm`.

The kwargs are as follows:

  * `maxit` determines the maximum number of iterations. If `logger` has a value >0, then the intermediate results are printed.
  * `errtype` determines the error type measured, see `adjust_for_errtype!`.
  * `stoptol` is the corresponding stopping tolerance.
  * `cref` is a `Vector{Tuple{Symbol,Int}}` that determines which coefficients of `graph` that are considered free variables and optimized.
  * `input` is the label corresponding to the input node of the graph.
  * The stepsize can be scaled with `γ0`.
  * `linlsqr` and `droptol` determines how the inner linear least squares problem is solved; see [`solve_linlsqr!`](@ref).
