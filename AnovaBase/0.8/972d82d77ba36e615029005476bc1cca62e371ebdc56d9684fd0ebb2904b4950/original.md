```
FullModel{M, N} <: AnovaModel{M, N}
```

A wrapper of a regression model for conducting ANOVA.

  * `M` is a type of regression model.
  * `N` is the number of predictors.

# Fields

  * `model`: a regression model.
  * `pred_id`: the index of terms included in ANOVA. The source iterable can be obtained by `predictors(model)`. This value may depend on `type` for certain model, e.g. type 1 ANOVA for a gamma regression model with inverse link.
  * `type`: type of ANOVA, either 1, 2 or 3.

# Constructor

```
FullModel(model::RegressionModel, type::Int, null::Bool, test_intercept::Bool)
```

  * `model`: a regression model.
  * `type`: type of ANOVA, either 1, 2 or 3.
  * `null`: whether `y ~ 0` is allowed.
  * `test_intercept`: whether intercept is going to be tested.
