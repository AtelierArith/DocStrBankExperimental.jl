```
lm(formula, data, allowrankdeficient=false;
   [wts::AbstractVector], dropcollinear::Bool=true)
lm(X::AbstractMatrix, y::AbstractVector;
   wts::AbstractVector=similar(y, 0), dropcollinear::Bool=true)
```

Fit a linear model to data. An alias for `fit(LinearModel, X, y; wts=wts, dropcollinear=dropcollinear)`

In the first method, `formula` must be a [StatsModels.jl `Formula` object](https://juliastats.org/StatsModels.jl/stable/formula/) and `data` a table (in the [Tables.jl](https://tables.juliadata.org/stable/) definition, e.g. a data frame). In the second method, `X` must be a matrix holding values of the independent variable(s) in columns (including if appropriate the intercept), and `y` must be a vector holding values of the dependent variable.

The keyword argument `wts` can be a `Vector` specifying frequency weights for observations. Such weights are equivalent to repeating each observation a number of times equal to its weight. Do note that this interpretation gives equal point estimates but different standard errors from analytical (a.k.a. inverse variance) weights and from probability (a.k.a. sampling) weights which are the default in some other software.

`dropcollinear` controls whether or not `lm` accepts a model matrix which is less-than-full rank. If `true` (the default), only the first of each set of linearly-dependent columns is used. The coefficient for redundant linearly dependent columns is `0.0` and all associated statistics are set to `NaN`.
