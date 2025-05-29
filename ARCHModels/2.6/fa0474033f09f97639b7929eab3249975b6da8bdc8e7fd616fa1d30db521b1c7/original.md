```
selectmodel(::Type{VS}, data; kwargs...) -> UnivariateARCHModel
```

Fit the volatility specification `VS` with varying lag lengths and return that which minimizes the [BIC](https://en.wikipedia.org/wiki/Bayesian_information_criterion).

# Keyword arguments:

  * `dist=StdNormal`: the error distribution.
  * `meanspec=Intercept`: the mean specification, either as a type or instance of that type.
  * `minlags=1`: minimum lag length to try in each parameter of `VS`.
  * `maxlags=3`: maximum lag length to try in each parameter of `VS`.
  * `criterion=bic`: function that takes a `UnivariateARCHModel` and returns the criterion to minimize.
  * `show_trace=false`: print `criterion` to screen for each estimated model.
  * `algorithm=BFGS(), autodiff=:forward, kwargs...`: passed on to the optimizer.

# Example

```
julia> selectmodel(EGARCH, BG96)

EGARCH{1, 1, 2} model with Gaussian errors, T=1974.

Mean equation parameters:
───────────────────────────────────────────────
      Estimate   Std.Error    z value  Pr(>|z|)
───────────────────────────────────────────────
μ  -0.00900018  0.00943948  -0.953461    0.3404
───────────────────────────────────────────────

Volatility parameters:
──────────────────────────────────────────────
      Estimate  Std.Error    z value  Pr(>|z|)
──────────────────────────────────────────────
ω   -0.0544398  0.0592073  -0.919478    0.3578
γ₁  -0.0243368  0.0270414  -0.899985    0.3681
β₁   0.960301   0.0388183  24.7384      <1e-99
α₁   0.405788   0.067466    6.0147      <1e-08
α₂  -0.207357   0.114161   -1.81636     0.0693
──────────────────────────────────────────────
```
