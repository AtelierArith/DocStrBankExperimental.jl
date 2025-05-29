```
check_gradient(M, F, gradF, p=rand(M), X=rand(M; vector_at=p); kwargs...)
```

Verify numerically whether the gradient `gradF(M,p)` of `F(M,p)` is correct, that is whether

$$
f(\operatorname{retr}_p(tX)) = f(p) + t⟨\operatorname{grad} f(p), X⟩ + \mathcal O(t^2)
$$

or in other words, that the error between the function $f$ and its first order Taylor behaves in error $\mathcal O(t^2)$, which indicates that the gradient is correct, cf. also [Boumal:2023; Section 4.8](@cite).

Note that if the errors are below the given tolerance and the method is exact, no plot is generated.

# Keyword arguments

  * `check_vector`:      (`true`) verify that $\operatorname{grad} f(p) ∈ T_p\mathcal M$ using `is_vector`.
  * `exactness_tol`:     (`1e-12`) if all errors are below this tolerance, the gradient is considered to be exact
  * `io`:                (`nothing`) provide an `IO` to print the result to
  * `gradient`:          (`grad_f(M, p)`) instead of the gradient function you can also provide the gradient at `p` directly
  * `limits`:            (`(1e-8,1)`) specify the limits in the `log_range`
  * `log_range`:         (`range(limits[1], limits[2]; length=N)`) - specify the range of points (in log scale) to sample the gradient line
  * `N`:                 (`101`) number of points to verify within the `log_range` default range $[10^{-8},10^{0}]$
  * `plot`:              (`false`) whether to plot the result (if `Plots.jl` is loaded). The plot is in log-log-scale. This is returned and can then also be saved.
  * `retraction_method`: (`default_retraction_method(M, typeof(p))`) retraction method to use
  * `slope_tol`:         (`0.1`) tolerance for the slope (global) of the approximation
  * `atol`, `rtol`:      (same defaults as `isapprox`) tolerances that are passed down to `is_vector` if `check_vector` is set to `true`
  * `error`:             (`:none`) how to handle errors, possible values: `:error`, `:info`, `:warn`
  * `window`:            (`nothing`) specify window sizes within the `log_range` that are used for the slope estimation. the default is, to use all window sizes `2:N`.

The remaining keyword arguments are also passed down to the `check_vector` call, such that tolerances can easily be set.
