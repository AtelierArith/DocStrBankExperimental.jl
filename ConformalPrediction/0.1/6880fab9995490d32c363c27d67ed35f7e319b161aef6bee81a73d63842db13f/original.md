```
MMI.predict(conf_model::NaiveRegressor, fitresult, Xnew)
```

For the [`NaiveRegressor`](@ref) prediction intervals are computed as follows:

$\hat{C}_{n,\alpha}(X_{n+1}) = \hat\mu(X_{n+1}) \pm \hat{q}_{n, \alpha}^{+} \{S_i^{\text{IS}} \}, \ i \in \mathcal{D}_{\text{train}}$

The naive approach typically produces prediction regions that undercover due to overfitting.
