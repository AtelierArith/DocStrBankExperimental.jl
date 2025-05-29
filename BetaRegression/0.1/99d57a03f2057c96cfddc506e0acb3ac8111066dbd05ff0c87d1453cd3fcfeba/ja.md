```
precisionlink(model::BetaRegressionModel)
```

精度 $\phi$ を推定された定数パラメータ $\theta_{p+1}$ にリンクするリンク関数 $h$ を返します。すなわち、$\phi = h^{-1}(\theta_{p+1})$ です。
