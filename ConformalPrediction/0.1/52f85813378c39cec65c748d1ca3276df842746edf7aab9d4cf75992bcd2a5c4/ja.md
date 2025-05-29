```
MMI.predict(conf_model::SimpleInductiveRegressor, fitresult, Xnew)
```

For the [`SimpleInductiveRegressor`](@ref) prediction intervals are computed as follows,

$$
\hat{C}_{n,\alpha}(X_{n+1}) = \hat\mu(X_{n+1}) \pm \hat{q}_{n, \alpha}^{+} \{S_i^{\text{CAL}} \}, \ i \in \mathcal{D}_{\text{calibration}}
$$

where $\mathcal{D}_{\text{calibration}}$ denotes the designated calibration data.
