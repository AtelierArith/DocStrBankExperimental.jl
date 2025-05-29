```
adjr2(model::StatisticalModel, variant::Symbol)
adjr²(model::StatisticalModel, variant::Symbol)
```

Adjusted pseudo-coefficient of determination (adjusted pseudo R-squared). For nonlinear models, one of the several pseudo R² definitions must be chosen via `variant`. The only currently supported variants are `:MacFadden`, defined as $1 - (\log (L) - k)/\log (L0)$ and `:devianceratio`, defined as $1 - (D/(n-k))/(D_0/(n-1))$. In these formulas, $L$ is the likelihood of the model, $L0$ that of the null model (the model including only the intercept), $D$ is the deviance of the model, $D_0$ is the deviance of the null model, $n$ is the number of observations (given by [`nobs`](@ref)) and $k$ is the number of consumed degrees of freedom of the model (as returned by [`dof`](@ref)).
