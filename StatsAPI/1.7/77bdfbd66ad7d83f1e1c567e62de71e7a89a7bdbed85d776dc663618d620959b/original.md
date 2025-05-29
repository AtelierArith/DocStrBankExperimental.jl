```
r2(model::StatisticalModel, variant::Symbol)
r²(model::StatisticalModel, variant::Symbol)
```

Pseudo-coefficient of determination (pseudo R-squared).

For nonlinear models, one of several pseudo R² definitions must be chosen via `variant`. Supported variants are:

  * `:MacFadden` (a.k.a. likelihood ratio index), defined as $1 - \log (L)/\log (L_0)$;
  * `:CoxSnell`, defined as $1 - (L_0/L)^{2/n}$;
  * `:Nagelkerke`, defined as $(1 - (L_0/L)^{2/n})/(1 - L_0^{2/n})$.
  * `:devianceratio`, defined as $1 - D/D_0$.

In the above formulas, $L$ is the likelihood of the model, $L_0$ is the likelihood of the null model (the model with only an intercept), $D$ is the deviance of the model (from the saturated model), $D_0$ is the deviance of the null model, $n$ is the number of observations (given by [`nobs`](@ref)).

The Cox-Snell and the deviance ratio variants both match the classical definition of R² for linear models.
