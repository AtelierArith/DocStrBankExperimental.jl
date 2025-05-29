```
MMI.predict(conf_model::CVPlusRegressor, fitresult, Xnew)
```

For the [`CVPlusRegressor`](@ref) prediction intervals are computed in much same way as for the [`JackknifePlusRegressor`](@ref). Specifically, we have,

$\hat{C}_{n,\alpha}(X_{n+1}) = \left[ \hat{q}_{n, \alpha}^{-} \{\hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) - S_i^{\text{CV}} \}, \hat{q}_{n, \alpha}^{+} \{\hat\mu_{-\mathcal{D}_{k(i)}}(X_{n+1}) + S_i^{\text{CV}}\} \right] , \ i \in \mathcal{D}_{\text{train}}$

where $\hat\mu_{-\mathcal{D}_{k(i)}}$ denotes the model fitted on training data with fold $\mathcal{D}_{k(i)}$ that contains the $i$ th point removed.

The [`JackknifePlusRegressor`](@ref) is a special case of the [`CVPlusRegressor`](@ref) for which $K=n$.
