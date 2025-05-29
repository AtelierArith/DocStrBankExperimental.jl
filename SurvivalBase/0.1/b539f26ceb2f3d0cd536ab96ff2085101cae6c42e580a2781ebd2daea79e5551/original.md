```
Surv(T::Symbol, Δ::Symbol)
```

Create a `SurvTerm` object that holds a tuple of variables `(T,Δ)` in the construction of a formula, usually on the left-hand-side, representing a right-censored output time `T` with its status indicatrix `Δ`: Δ being true means that the time was indeed observed, while false means censoring. 

This information, usually on the left hand side a formula, has then a behavior that may depend on the estimator. It allows to use formulas from [`StatsModels.jl`](https://github.com/JuliaStats/StatsModels.jl) as follow: 

```
@formula(Surv(time,status) ~ covariate1 + covariate 2)
```

This usage is common in, e.g., cox models. However, note that the *meaning* of the formula heavily depends on the model : for hazard regession and maximum likelyhood estimation, this does not mean the same thing. 
