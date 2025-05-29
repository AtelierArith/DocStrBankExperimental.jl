```
fit(VS::Type{<:UnivariateVolatilitySpec}, data; dist=StdNormal, meanspec=Intercept,
    algorithm=BFGS(), autodiff=:forward, kwargs...)
```

Fit the ARCH model specified by `VS` to `data`. `data` can be a vector or a GLM.LinearModel (or GLM.TableRegressionModel).

# Keyword arguments:

  * `dist=StdNormal`: the error distribution.
  * `meanspec=Intercept`: the mean specification, either as a type or instance of that type.
  * `algorithm=BFGS(), autodiff=:forward, kwargs...`: passed on to the optimizer.

# Example: EGARCH{1, 1, 1} model without intercept, Student's t errors.

```jldoctest
julia> fit(EGARCH{1, 1, 1}, BG96; meanspec=NoIntercept, dist=StdT)

EGARCH{1, 1, 1} model with Student's t errors, T=1974.


Volatility parameters:
──────────────────────────────────────────────
      Estimate  Std.Error    z value  Pr(>|z|)
──────────────────────────────────────────────
ω   -0.0162014  0.0186806  -0.867286    0.3858
γ₁  -0.0378454  0.018024   -2.09972     0.0358
β₁   0.977687   0.012558   77.8538      <1e-99
α₁   0.255804   0.0625497   4.08961     <1e-04
──────────────────────────────────────────────

Distribution parameters:
─────────────────────────────────────────
   Estimate  Std.Error  z value  Pr(>|z|)
─────────────────────────────────────────
ν   4.12423    0.40059  10.2954    <1e-24
─────────────────────────────────────────
```
