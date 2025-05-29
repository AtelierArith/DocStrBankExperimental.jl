```
coeftable(obj::EconometricModel;
	  level::Real = 0.95)
coeftable(obj::EconometricModel{<:LinearModelEstimators};
	  level::Real = 0.95,
	  vce::VCE = obj.vce)
```

Return a table of class `CoefTable` with coefficients and related statistics. `level` determines the level for confidence intervals (by default, 95%). `vce` determines the variance-covariance estimator (by default, `OIM`).
