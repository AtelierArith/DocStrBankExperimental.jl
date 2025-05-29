```
MMI.predict(conf_model::CVMinMaxRegressor, fitresult, Xnew)
```

For the [`CVMinMaxRegressor`](@ref) prediction intervals are computed as follows,

$\hat{C}_{n,\alpha}(X_{n+1}) = \left[ \min_{i=1,...,n} \hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) -  \hat{q}_{n, \alpha}^{+} \{S_i^{\text{CV}} \}, \max_{i=1,...,n} \hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) + \hat{q}_{n, \alpha}^{+} \{ S_i^{\text{CV}}\} \right] , i \in \mathcal{D}_{\text{train}}$

where $\hat\mu_{-\mathcal{D}_{k(i)}}$ denotes the model fitted on training data with subset $\mathcal{D}_{k(i)}$ that contains the $i$ th point removed.
