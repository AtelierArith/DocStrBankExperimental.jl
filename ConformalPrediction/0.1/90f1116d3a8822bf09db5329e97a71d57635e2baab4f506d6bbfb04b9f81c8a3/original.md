```
MMI.predict(conf_model::AdaptiveInductiveClassifier, fitresult, Xnew)
```

For the [`AdaptiveInductiveClassifier`](@ref) prediction sets are computed as follows,

$\hat{C}_{n,\alpha}(X_{n+1}) = \left\{y: s(X_{n+1},y) \le \hat{q}_{n, \alpha}^{+} \{S_i^{\text{CAL}}\} \right\},  i \in \mathcal{D}_{\text{calibration}}$

where $\mathcal{D}_{\text{calibration}}$ denotes the designated calibration data.
