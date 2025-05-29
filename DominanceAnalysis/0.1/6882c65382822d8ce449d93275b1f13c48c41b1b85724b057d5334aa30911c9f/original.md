```
dominance(df::AbstractDataFrame, dep::Symbol, indeps::Vector; 
    covars = [], fitstat = :McFadden, link = nothing, family = nothing,
    multithreads = true, wts = nothing)
```

Performs dominance analysis. 

## Options:

```
- df - input DataFrame
- dep - dependent variable (Symbol only)
- indeps - a vector of Symbols or tuple of Symbols. Tuples are used to create sets of variables
- covars - covariates to be included in all models. These variables are not used in dominance analysis
- fitstat - R2 variant to be used for GLM models. Currently, :McFadden (default) and :Nagelkerke are available
- link - link function for GLM models. If it is not set, a canonical link function will be chosen.
- family - required for GLM models.
- multithreads - set it to `false` to turn off multithreading
- wts - a vector of weights for weighted regressions
```
