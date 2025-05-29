```julia
FrequentistRegression(::Symbol, model, formula, link = GLM.IdentityLink)
```

Constructor for `FrequentistRegression`. `model` can be any regression model. Used by `fit` functions to return a frequentist regression model container.
