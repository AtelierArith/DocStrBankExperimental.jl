```
MLESettings(y, model, init, optimizer, ci)
```

Wrapper function to specify estimation settings.

  * `y`: Time series
  * `model`: Model specification
  * `init`: Initial values (vector or parameter).
  * `optimizer`: Optimization routine. "BFGS", "LBFGS" or "NelderMead"
  * `ci`: Indicator: Shall confidence intervals be computed?
  * `maxEval`: Maximum number of likelihood evaluations

# Example

```julia-repl
MLESettings(y, model, ci = true, maxEval = 1e9)
```

If the argument `init` is not given, valid initial values are chosen. See also [MLEControl](@ref).
