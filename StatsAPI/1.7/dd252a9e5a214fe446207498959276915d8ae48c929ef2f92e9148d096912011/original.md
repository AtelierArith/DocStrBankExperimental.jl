```
bic(model::StatisticalModel)
```

Bayesian Information Criterion, defined as $-2 \log L + k \log n$, with $L$ the likelihood of the model,  $k$ its number of consumed degrees of freedom (as returned by [`dof`](@ref)), and $n$ the number of observations (as returned by [`nobs`](@ref)).
