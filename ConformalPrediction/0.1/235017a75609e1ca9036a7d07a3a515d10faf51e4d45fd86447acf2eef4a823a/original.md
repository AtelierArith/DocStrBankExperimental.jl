```
MMI.predict(conf_model::JackknifeRegressor, fitresult, Xnew)
```

For the [`JackknifeRegressor`](@ref) prediction intervals are computed as follows,

$\hat{C}_{n,\alpha}(X_{n+1}) = \hat\mu(X_{n+1}) \pm \hat{q}_{n, \alpha}^{+} \{S_i^{\text{LOO}}\}, \ i \in \mathcal{D}_{\text{train}}$

where $S_i^{\text{LOO}}$ denotes the nonconformity that is generated as explained in [`fit(conf_model::JackknifeRegressor, verbosity, X, y)`](@ref). The jackknife procedure addresses the overfitting issue associated with the [`NaiveRegressor`](@ref).
