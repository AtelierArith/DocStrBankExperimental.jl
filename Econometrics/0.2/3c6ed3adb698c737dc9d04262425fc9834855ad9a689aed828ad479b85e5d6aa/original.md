```
stderror(obj::EconometricModel)
stderror(obj::EconometricModel{<:LinearModelEstimators}, vce::VCE = obj.vce)
```

Return the standard errors for the coefficients of the model. The `vce` argument allows to request variance estimators.
