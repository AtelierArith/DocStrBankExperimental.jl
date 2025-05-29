```
bifurcation_data(model::UDE;N=25)
```

Calcualtes the equilibrium values of the state variabels $y_t$ as a function of the covariates `X_t` and return the value in a data frame. The funciton calcualtes the equilibrium values on a grid of $N$ evenly spaced point for each covariate.
