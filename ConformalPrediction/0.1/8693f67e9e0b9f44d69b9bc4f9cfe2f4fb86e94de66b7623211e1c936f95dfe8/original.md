```
MMI.predict(conf_model::ConformalQuantileRegressor, fitresult, Xnew)
```

For the [`ConformalQuantileRegressor`](@ref) prediction intervals are computed as follows,

$\hat{C}_{n,\alpha}(X_{n+1}) = [\hat\mu_{\alpha_{lo}}(X_{n+1}) - \hat{q}_{n, \alpha} \{S_i^{\text{CAL}} \}, \hat\mu_{\alpha_{hi}}(X_{n+1}) + \hat{q}_{n, \alpha} \{S_i^{\text{CAL}} \}], \ i \in \mathcal{D}_{\text{calibration}}$

where $\mathcal{D}_{\text{calibration}}$ denotes the designated calibration data.
