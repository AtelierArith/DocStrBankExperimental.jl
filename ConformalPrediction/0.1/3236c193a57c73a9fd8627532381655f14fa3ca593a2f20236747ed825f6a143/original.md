```
MMI.fit(conf_model::AdaptiveInductiveClassifier, verbosity, X, y)
```

For the [`AdaptiveInductiveClassifier`](@ref) nonconformity scores are computed by cumulatively summing the ranked scores of each label in descending order until reaching the true label $Y_i$:

$S_i^{\text{CAL}} = s(X_i,Y_i) = \sum_{j=1}^k  \hat\mu(X_i)_{\pi_j} \ \text{where } \ Y_i=\pi_k,  i \in \mathcal{D}_{\text{calibration}}$
