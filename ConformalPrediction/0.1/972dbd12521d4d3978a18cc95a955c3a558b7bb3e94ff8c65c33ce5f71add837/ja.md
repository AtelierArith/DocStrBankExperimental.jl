```
MMI.predict(conf_model::TimeSeriesRegressorEnsembleBatch, fitresult, Xnew)
```

For the [`TimeSeriesRegressorEnsembleBatch`](@ref) prediction intervals are computed as follows,

$$
\hat{C}_{n,\alpha, B}^{J+ab}(X_{n+1}) = \left[ \hat{q}_{n, \alpha}^{-} \{\hat\mu_{agg(-i)}(X_{n+1}) - S_i^{\text{J+ab}} \}, \hat{q}_{n, \alpha}^{+} \{\hat\mu_{agg(-i)}(X_{n+1}) + S_i^{\text{J+ab}}\} \right] , i \in \mathcal{D}_{\text{train}}
$$

where $\hat\mu_{agg(-i)}$ denotes the aggregated models $\hat\mu_{1}, ...., \hat\mu_{B}$ fitted on bootstrapped data (B) does not include the $i$th data point. The jackknife$+$ procedure is more stable than the [`JackknifeRegressor`](@ref).
