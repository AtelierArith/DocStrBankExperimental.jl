```
ftest(mod::LinearModel...; atol::Real=0.0)
```

For each sequential pair of linear models in `mod...`, perform an F-test to determine if the one model fits significantly better than the other. Models must have been fitted on the same data, and be nested either in forward or backward direction.

A table is returned containing consumed degrees of freedom (DOF), difference in DOF from the preceding model, sum of squared residuals (SSR), difference in SSR from the preceding model, R², difference in R² from the preceding model, and F-statistic and p-value for the comparison between the two models.

!!! note
    This function can be used to perform an ANOVA by testing the relative fit of two models to the data


Optional keyword argument `atol` controls the numerical tolerance when testing whether the models are nested.

# Examples

Suppose we want to compare the effects of two or more treatments on some result. Because this is an ANOVA, our null hypothesis is that `Result ~ 1` fits the data as well as `Result ~ 1 + Treatment`.

```jldoctest ; setup = :(using CategoricalArrays, DataFrames, GLM)
julia> dat = DataFrame(Result=[1.1, 1.2, 1, 2.2, 1.9, 2, 0.9, 1, 1, 2.2, 2, 2],
                       Treatment=[1, 1, 1, 2, 2, 2, 1, 1, 1, 2, 2, 2],
                       Other=categorical([1, 1, 2, 1, 2, 1, 3, 1, 1, 2, 2, 1]));


julia> nullmodel = lm(@formula(Result ~ 1), dat);


julia> model = lm(@formula(Result ~ 1 + Treatment), dat);


julia> bigmodel = lm(@formula(Result ~ 1 + Treatment + Other), dat);


julia> ftest(nullmodel.model, model.model)
F-test: 2 models fitted on 12 observations
─────────────────────────────────────────────────────────────────
     DOF  ΔDOF     SSR     ΔSSR      R²     ΔR²        F*   p(>F)
─────────────────────────────────────────────────────────────────
[1]    2        3.2292           0.0000
[2]    3     1  0.1283  -3.1008  0.9603  0.9603  241.6234  <1e-07
─────────────────────────────────────────────────────────────────

julia> ftest(nullmodel.model, model.model, bigmodel.model)
F-test: 3 models fitted on 12 observations
─────────────────────────────────────────────────────────────────
     DOF  ΔDOF     SSR     ΔSSR      R²     ΔR²        F*   p(>F)
─────────────────────────────────────────────────────────────────
[1]    2        3.2292           0.0000
[2]    3     1  0.1283  -3.1008  0.9603  0.9603  241.6234  <1e-07
[3]    5     2  0.1017  -0.0266  0.9685  0.0082    1.0456  0.3950
─────────────────────────────────────────────────────────────────
```
