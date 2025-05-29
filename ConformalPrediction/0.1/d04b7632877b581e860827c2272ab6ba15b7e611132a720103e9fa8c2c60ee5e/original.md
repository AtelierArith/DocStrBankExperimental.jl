```
MMI.fit(conf_model::JackknifePlusMinMaxAbRegressor, verbosity, X, y)
```

For the [`JackknifePlusAbMinMaxRegressor`](@ref) nonconformity scores are as,

$S_i^{\text{J+MinMax}} = s(X_i, Y_i) = h(agg(\hat\mu_{B_{K(-i)}}(X_i)), Y_i), \ i \in \mathcal{D}_{\text{train}}$

where $agg(\hat\mu_{B_{K(-i)}}(X_i))$ denotes the aggregate predictions, typically mean or median, for each $X_i$ (with $K_{-i}$ the bootstraps not containing $X_i$). In other words, B models are trained on boostrapped sampling, the fitted models are then used to create aggregated prediction of out-of-sample $X_i$. The corresponding nonconformity score is then computed by applying a heuristic uncertainty measure $h(\cdot)$ to the fitted value $agg(\hat\mu_{B_{K(-i)}}(X_i))$ and the true value $Y_i$.
