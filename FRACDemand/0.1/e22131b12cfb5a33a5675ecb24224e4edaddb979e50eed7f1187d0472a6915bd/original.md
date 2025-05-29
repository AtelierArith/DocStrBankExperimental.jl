```
function get_FEs(problem::FRACProblem)
```

This is an internal function which is used to estimate fixed effects at constrained estimates. We estimate fixed effects by residualizing the  outcome variable at the constrained estimates and then regressing the residuals on fixed effects.
