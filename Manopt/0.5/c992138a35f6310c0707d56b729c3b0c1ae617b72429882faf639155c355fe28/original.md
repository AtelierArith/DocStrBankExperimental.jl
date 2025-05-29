```
check_Hessian(M, f, grad_f, Hess_f, p=rand(M), X=rand(M; vector_at=p), Y=rand(M, vector_at=p); kwargs...)
```

Verify numerically whether the Hessian `Hess_f(M,p, X)` of `f(M,p)` is correct.

For this either a second-order retraction or a critical point $p$ of `f` is required. The approximation is then

$$
f(\operatorname{retr}_p(tX)) = f(p) + t⟨\operatorname{grad} f(p), X⟩ + \frac{t^2}{2}⟨\operatorname{Hess}f(p)[X], X⟩ + \mathcal O(t^3)
$$

or in other words, that the error between the function $f$ and its second order Taylor behaves in error $\mathcal O(t^3)$, which indicates that the Hessian is correct, cf. also [Boumal:2023; Section 6.8](@cite).

Note that if the errors are below the given tolerance and the method is exact, no plot is generated.

# Keyword arguments

  * `check_grad=true`: verify that $\operatorname{grad}f(p) ∈ T_{p}\mathcal M$.
  * `check_linearity=true`: verify that the Hessian is linear, see [`is_Hessian_linear`](@ref) using `a`, `b`, `X`, and `Y`
  * `check_symmetry=true`: verify that the Hessian is symmetric, see [`is_Hessian_symmetric`](@ref)
  * `check_vector=false`: verify that `\operatorname{Hess} f(p)[X] ∈ T_{p}\mathcal M``using`is_vector`.
  * `mode=:Default`: specify the mode for the verification; the default assumption is, that the retraction provided is of second order. Otherwise one can also verify the Hessian if the point `p` is a critical point. THen set the mode to `:CritalPoint` to use [`gradient_descent`](@ref) to find a critical point. Note: this requires (and evaluates) new tangent vectors `X` and `Y`
  * `atol`, `rtol`:      (same defaults as `isapprox`) tolerances that are passed down to all checks
  * `a`, `b`            two real values to verify linearity of the Hessian (if `check_linearity=true`)
  * `N=101`: number of points to verify within the `log_range` default range $[10^{-8},10^{0}]$
  * `exactness_tol=1e-12`: if all errors are below this tolerance, the verification is considered to be exact
  * `io=nothing`: provide an `IO` to print the result to
  * `gradient=grad_f(M, p)`: instead of the gradient function you can also provide the gradient at `p` directly
  * `Hessian=Hess_f(M, p, X)`: instead of the Hessian function you can provide the result of $\operatorname{Hess} f(p)[X]$ directly. Note that evaluations of the Hessian might still be necessary for checking linearity and symmetry and/or when using `:CriticalPoint` mode.
  * `limits=(-8.0, 0.0)`: specify the limits in the `log_range`
  * `log_range=range(limits[1], limits[2]; length=N)`: specify the range of points (in log scale) to sample the Hessian line
  * `N=101`: number of points to use within the `log_range` default range $[10^{-8},10^{0}]$
  * `plot=false`: whether to plot the resulting verification (requires `Plots.jl` to be loaded). The plot is in log-log-scale. This is returned and can then also be saved.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `slope_tol=0.1`: tolerance for the slope (global) of the approximation
  * `error=:none`: how to handle errors, possible values: `:error`, `:info`, `:warn`
  * `window=nothing`: specify window sizes within the `log_range` that are used for the slope estimation. the default is, to use all window sizes `2:N`.

The `kwargs...` are also passed down to the `check_vector` and the `check_gradient` call, such that tolerances can easily be set.

While `check_vector` is also passed to the inner call to `check_gradient` as well as the `retraction_method`, this inner `check_gradient` is meant to be just for inner verification, so it does not throw an error nor produce a plot itself.
