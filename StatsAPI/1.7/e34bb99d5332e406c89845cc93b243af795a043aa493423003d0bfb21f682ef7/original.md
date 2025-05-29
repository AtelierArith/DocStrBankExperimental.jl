```
aicc(model::StatisticalModel)
```

Corrected Akaike's Information Criterion for small sample sizes (Hurvich and Tsai 1989), defined as $-2 \log L + 2k + 2k(k-1)/(n-k-1)$, with $L$ the likelihood of the model, $k$ its number of consumed degrees of freedom (as returned by [`dof`](@ref)), and $n$ the number of observations (as returned by [`nobs`](@ref)).
