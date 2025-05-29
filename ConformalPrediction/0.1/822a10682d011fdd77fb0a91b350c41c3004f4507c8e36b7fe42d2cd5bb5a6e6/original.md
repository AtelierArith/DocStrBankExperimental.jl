```
MMI.fit(conf_model::ConformalQuantileRegressor, verbosity, X, y)
```

For the [`ConformalQuantileRegressor`](@ref) nonconformity scores are computed as follows:

$S_i^{\text{CAL}} = s(X_i, Y_i) = h(\hat\mu_{\alpha_{lo}}(X_i), \hat\mu_{\alpha_{hi}}(X_i)  ,Y_i), \ i \in \mathcal{D}_{\text{calibration}}$

A typical choice for the heuristic function is $h(\hat\mu_{\alpha_{lo}}(X_i), \hat\mu_{\alpha_{hi}}(X_i)  ,Y_i)= max\{\hat\mu_{\alpha_{low}}(X_i)-Y_i, Y_i-\hat\mu_{\alpha_{hi}}(X_i)\}$ where $\hat\mu$ denotes the model fitted on training data $\mathcal{D}_{\text{train}}` and$\alpha*{lo}, \alpha*{hi}`` lower and higher percentile.
