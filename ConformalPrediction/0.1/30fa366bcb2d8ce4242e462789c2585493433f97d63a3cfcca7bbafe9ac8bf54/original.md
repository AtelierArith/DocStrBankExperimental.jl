```
MMI.predict(conf_model::JackknifePlusAbMinMaxRegressor, fitresult, Xnew)
```

For the [`JackknifePlusAbMinMaxRegressor`](@ref) prediction intervals are computed as follows,

$\hat{C}_{n,\alpha}^{J+MinMax}(X_{n+1}) = \left[ \min_{i=1,...,n} \hat\mu_{-i}(X_{n+1}) -  \hat{q}_{n, \alpha}^{+} \{S_i^{\text{J+MinMax}} \}, \max_{i=1,...,n} \hat\mu_{-i}(X_{n+1}) + \hat{q}_{n, \alpha}^{+} \{S_i^{\text{J+MinMax}}\} \right] ,  i \in \mathcal{D}_{\text{train}}$

where $\hat\mu_{-i}$ denotes the model fitted on training data with $i$th point removed. The jackknife+ab-minmax procedure is more conservative than the [`JackknifePlusAbRegressor`](@ref).
