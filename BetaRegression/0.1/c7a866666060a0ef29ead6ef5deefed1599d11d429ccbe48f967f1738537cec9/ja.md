```
devresid(model::BetaRegressionModel)
```

モデルの符号付き逸脱残差を計算します。

$$
\mathrm{sgn}(y_i - \hat{y}_i) \sqrt{2 \lvert \ell(y_i, \hat{\phi}) - \ell(\hat{y}_i, \hat{\phi}) \rvert}
$$

ここで、$\ell$は対数尤度を示し、$y_i$は応答の$i$番目の観測値、$\hat{y}_i$は$i$番目のフィッティング値、$\hat{\phi}$は推定された共通精度パラメータです。

参照: [`deviance`](@ref)
