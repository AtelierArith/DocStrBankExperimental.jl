```
MLEControl(init::parameter, optimizer::String, ci::Bool, maxEval::Int64)
```

Structure for esitmation settings.

  * `init`: Initial values for optimization
  * `optimizer`: Optimizing Routine, "NelderMead", "BFGS" or "LBFGS"
  * `ci`: Indicator: Shall confidence intervals be computed?
  * `maxEval`: Maximum number of likelihood evaluations
