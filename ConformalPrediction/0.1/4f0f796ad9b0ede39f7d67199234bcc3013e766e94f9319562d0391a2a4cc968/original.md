```
MMI.fit(conf_model::NaiveRegressor, verbosity, X, y)
```

For the [`NaiveRegressor`](@ref) nonconformity scores are computed in-sample as follows:

$S_i^{\text{IS}} = s(X_i, Y_i) = h(\hat\mu(X_i), Y_i), \ i \in \mathcal{D}_{\text{train}}$

A typical choice for the heuristic function is $h(\hat\mu(X_i),Y_i)=|Y_i-\hat\mu(X_i)|$ where $\hat\mu$ denotes the model fitted on training data $\mathcal{D}_{\text{train}}$.
