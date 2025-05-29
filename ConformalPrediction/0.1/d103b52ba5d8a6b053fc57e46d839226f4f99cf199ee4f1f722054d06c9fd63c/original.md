```
MMI.predict(conf_model::JackknifePlusRegressor, fitresult, Xnew)
```

For the [`JackknifePlusRegressor`](@ref) prediction intervals are computed as follows,

$\hat{C}_{n,\alpha}(X_{n+1}) = \left[ \hat{q}_{n, \alpha}^{-} \{\hat\mu_{-i}(X_{n+1}) - S_i^{\text{LOO}} \}, \hat{q}_{n, \alpha}^{+} \{\hat\mu_{-i}(X_{n+1}) + S_i^{\text{LOO}}\} \right] , i \in \mathcal{D}_{\text{train}}$

where $\hat\mu_{-i}$ denotes the model fitted on training data with $i$th point removed. The jackknife$+$ procedure is more stable than the [`JackknifeRegressor`](@ref).
