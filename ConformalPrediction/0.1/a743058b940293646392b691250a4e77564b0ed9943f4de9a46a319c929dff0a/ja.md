```
MMI.predict(conf_model::SimpleInductiveClassifier, fitresult, Xnew)
```

[`SimpleInductiveClassifier`](@ref) の予測は次のように計算されます。

$$
\hat{C}_{n,\alpha}(X_{n+1}) = \left\{y: s(X_{n+1},y) \le \hat{q}_{n, \alpha}^{+} \{S_i^{\text{CAL}}\} \right\}, \ i \in \mathcal{D}_{\text{calibration}}
$$

ここで、$\mathcal{D}_{\text{calibration}}$ は指定されたキャリブレーションデータを示します。
