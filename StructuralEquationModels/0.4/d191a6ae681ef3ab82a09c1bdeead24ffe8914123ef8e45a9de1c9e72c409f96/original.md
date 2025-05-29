```
se_hessian(fit::SemFit; method = :finitediff)
```

Return hessian-based standard errors.

# Arguments

  * `method`: how to compute the hessian. Options are

      * `:analytic`: (only if an analytic hessian for the model can be computed)
      * `:finitediff`: for finite difference approximation
