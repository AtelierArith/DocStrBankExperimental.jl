```
build_model(model_equations::AbstractString,R=false; df::AbstractFloat=4.0)
```

  * Build a model from **model equations** with the residual variance **R**. In Bayesian analysis, **R** is the mean for the prior assigned for the residual variance with degree of freedom **df**, defaulting to 4.0. If **R** is not provided, a value is calculated from responses (phenotypes).
  * By default, all variabels in model*equations are factors (categorical) and fixed. Set variables to be covariates (continuous) or random using functions `set*covariate()`or`set_random()`.

```julia
#single-trait
model_equations = "BW = intercept + age + sex"
R               = 6.72
models          = build_model(model_equations,R);

#multi-trait
model_equations = "BW = intercept + age + sex
                   CW = intercept + litter";
R               = [6.72   24.84
                   24.84  708.41]
models          = build_model(model_equations,R);
```
