```
PLProblem{T,probType,P,PF,PR}
```

Defines a profile likelihood problem.

## Mathematical Specification of a Profile Likelihood Problem:

A profile likelihood problem is defined by 

  * an objective function (usually negative log-likelihood function) wrapped within an `optprob::OptimizationProblem`. Consult [Optimization.jl docs](https://docs.sciml.ai/Optimization/stable/API/optimization_problem/) for details.
  * a set of optimal values of the parameters `optpars` that minimize the objective function.

### Constructors

```julia
PLProblem(optprob, optpars, profile_range = tuple.(optprob.lb, optprob.ub); 
  conf_level = 0.95, df = 1, threshold = chi2_quantile(conf_level, df))
```

### Arguments

  * `optprob`: The `OptimizationProblem` to be solved.
  * `optpars`: Initial (optimal) values of the parameters.
  * `profile_range`: The range over which the profile likelihood is computed. Defaults to `tuple.(lb,ub)` of the `OptimizationProblem`.

### Keyword arguments

  * `conf_level`: The confidence level for the profile likelihood. Defaults to `0.95`.
  * `df`: The degrees of freedom for the profile likelihood. Defaults to `1`.
  * `threshold`: The threshold for the profile likelihood. Can be set to `Inf` if confidence interval endpoint estimation is not required. Defaults to `chi2_quantile(conf_level, df)`.
