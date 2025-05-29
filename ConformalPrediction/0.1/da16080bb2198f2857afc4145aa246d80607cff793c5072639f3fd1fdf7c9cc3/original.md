```
MMI.predict(conf_model::NaiveClassifier, fitresult, Xnew)
```

For the [`NaiveClassifier`](@ref) prediction sets are computed as follows:

$\hat{C}_{n,\alpha}(X_{n+1}) = \left\{y: s(X_{n+1},y) \le \hat{q}_{n, \alpha}^{+} \{S_i^{\text{IS}} \} \right\}, \ i \in \mathcal{D}_{\text{train}}$

The naive approach typically produces prediction regions that undercover due to overfitting.
