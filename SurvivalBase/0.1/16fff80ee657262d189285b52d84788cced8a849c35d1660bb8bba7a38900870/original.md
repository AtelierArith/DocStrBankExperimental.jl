```
Strata(x::Symbol)
```

Create a `StrataTerm` object that holds a variable in the construction of a formula to stratify an estimator. 

The behavior of the stratification depends on the fitted estimator: is is usally used on the right hand side of formulas from [`StatsModels.jl`](https://github.com/JuliaStats/StatsModels.jl) as

```
@formula(Surv(time,status) ~ Strata(covariate1) + covariate 2)
```

It then has a behavior that unufortunately heavily depends on the estimator, e.g. stratification of a log-rank-type test. 
