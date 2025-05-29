```
mutable struct LinearRegressionResult
```

# Fields

  * `lm::Any`: Regression result
  * `r2::Number`: Adjusted R square
  * `inter::Number`: Intercept of fitting
  * `slope::Number`: Slope of fitting
  * `inter_p::Number`: P value of intercept
  * `slope_p::Number`: P value of slopes
  * `inter_ci::Array`: Confidence interval of intercept
  * `slope_ci::Array`: Confidence interval of slopes
  * `df::DataFrames.DataFrame`: Predictions DataFrame
