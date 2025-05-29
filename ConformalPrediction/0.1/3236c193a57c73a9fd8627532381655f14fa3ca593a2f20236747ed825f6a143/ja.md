```
MMI.fit(conf_model::AdaptiveInductiveClassifier, verbosity, X, y)
```

[`AdaptiveInductiveClassifier`](@ref) の非適合性スコアは、真のラベル $Y_i$ に達するまで、各ラベルのランク付けされたスコアを降順に累積して合計することによって計算されます：

$$
S_i^{\text{CAL}} = s(X_i,Y_i) = \sum_{j=1}^k  \hat\mu(X_i)_{\pi_j} \ \text{where } \ Y_i=\pi_k,  i \in \mathcal{D}_{\text{calibration}}
$$
