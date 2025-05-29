```
fit(DRE, x_nu, x_de, ranges; [optlib])
```

Perform hyperparameter tuning of density ratio estimator `dre` with numerator and denominator samples, `x_nu` and `x_de` and with hyperparameter `ranges`. Optionally, specify the optimization library `optlib`.

### Notes

Hyperparameter tuning is not defined for all density ratio estimators. Therefore, this function may not work with some estimators.
