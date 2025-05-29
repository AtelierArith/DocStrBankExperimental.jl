```
MMI.predict(conf_model::ConformalQuantileRegressor, fitresult, Xnew)
```

For the [`ConformalQuantileRegressor`](@ref) 予測区間は次のように計算されます、

$$
\hat{C}_{n,\alpha}(X_{n+1}) = [\hat\mu_{\alpha_{lo}}(X_{n+1}) - \hat{q}_{n, \alpha} \{S_i^{\text{CAL}} \}, \hat\mu_{\alpha_{hi}}(X_{n+1}) + \hat{q}_{n, \alpha} \{S_i^{\text{CAL}} \}], \ i \in \mathcal{D}_{\text{calibration}}
$$

ここで、$\mathcal{D}_{\text{calibration}}$ は指定されたキャリブレーションデータを示します。
