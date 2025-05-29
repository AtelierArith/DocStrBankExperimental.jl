```
aic(model::StatisticalModel)
```

Akaike's Information Criterion, defined as $-2 \log L + 2k$, with $L$ the likelihood of the model, and `k` its number of consumed degrees of freedom (as returned by [`dof`](@ref)).
