```julia
transform_logdensity(t, f, x)

```

Let $y = t(x)$, and $f(y)$ a log density at `y`. This function evaluates `f ∘ t` as a log density, taking care of the log Jacobian correction.
