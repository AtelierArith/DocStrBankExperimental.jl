```
vcov(obj::EconometricModel)
vcov(obj::EconometricModel{<:LinearModelEstimators}, vce::VCE = obj.vce)
```

Return the variance-covariance matrix for the coefficients of the model. The `vce` argument allows to request variance estimators.
