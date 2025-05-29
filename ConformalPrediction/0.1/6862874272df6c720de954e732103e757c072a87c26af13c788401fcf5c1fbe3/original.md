```
MMI.fit(conf_model::CVPlusRegressor, verbosity, X, y)
```

For the [`CVPlusRegressor`](@ref) nonconformity scores are computed though cross-validation (CV) as follows,

$S_i^{\text{CV}} = s(X_i, Y_i) = h(\hat\mu_{-\mathcal{D}_{k(i)}}(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}$

where $\hat\mu_{-\mathcal{D}_{k(i)}}(X_i)$ denotes the CV prediction for $X_i$. In other words, for each CV fold $k=1,...,K$ and each training instance $i=1,...,n$ the model is trained on all training data excluding the fold containing $i$. The fitted model is then used to predict out-of-sample from $X_i$. The corresponding nonconformity score is then computed by applying a heuristic uncertainty measure $h(\cdot)$ to the fitted value $\hat\mu_{-\mathcal{D}_{k(i)}}(X_i)$ and the true value $Y_i$.
