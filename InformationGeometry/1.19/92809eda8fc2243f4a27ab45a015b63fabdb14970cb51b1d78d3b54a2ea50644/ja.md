```
GeneralizedDOF(DM::AbstractDataModel)
```

与えられた `DataModel` の一般化自由度を計算します。これは非整数値を取ることができ、次の定義に基づいています: https://doi.org/10.1093/biomet/asv019 https://doi.org/10.2307/2669609 その定義は、期待予測誤差 (EPE) が残差平方和 (RSS) によって `2σ^2 * dof` の量だけ過大評価されるという事実に基づいています。これは $\sum_{i=1}^{n} \partial \hat{y}_i / \partial {y_\text{data}}_i$ として計算できます。
