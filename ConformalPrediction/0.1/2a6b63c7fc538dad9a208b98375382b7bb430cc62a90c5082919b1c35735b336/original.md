```
MMI.fit(conf_model::CVMinMaxRegressor, verbosity, X, y)
```

For the [`CVMinMaxRegressor`](@ref) nonconformity scores are computed in the same way as for the [`CVPlusRegressor`](@ref). Specifically, we have,

$S_i^{\text{CV}} = s(X_i, Y_i) = h(\hat\mu_{-\mathcal{D}_{k(i)}}(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}$

where $\hat\mu_{-\mathcal{D}_{k(i)}}(X_i)$ denotes the CV prediction for $X_i$. In other words, for each CV fold $k=1,...,K$ and each training instance $i=1,...,n$ the model is trained on all training data excluding the fold containing $i$. The fitted model is then used to predict out-of-sample from $X_i$. The corresponding nonconformity score is then computed by applying a heuristic uncertainty measure $h(\cdot)$ to the fitted value $\hat\mu_{-\mathcal{D}_{k(i)}}(X_i)$ and the true value $Y_i$.
