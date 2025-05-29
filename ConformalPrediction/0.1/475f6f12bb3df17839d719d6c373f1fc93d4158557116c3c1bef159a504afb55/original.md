```
MMI.fit(conf_model::JackknifeRegressor, verbosity, X, y)
```

For the [`JackknifeRegressor`](@ref) nonconformity scores are computed through a leave-one-out (LOO) procedure as follows,

$S_i^{\text{LOO}} = s(X_i, Y_i) = h(\hat\mu_{-i}(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}$

where $\hat\mu_{-i}(X_i)$ denotes the leave-one-out prediction for $X_i$. In other words, for each training instance $i=1,...,n$ the model is trained on all training data excluding $i$. The fitted model is then used to predict out-of-sample from $X_i$. The corresponding nonconformity score is then computed by applying a heuristic uncertainty measure $h(\cdot)$ to the fitted value $\hat\mu_{-i}(X_i)$ and the true value $Y_i$.
