```
coeftable(model::BetaRegressionModel; level=0.95)
```

モデルパラメータの点推定値、そのそれぞれの標準誤差、$z$-統計量、Wald $p$-値、および指定された`level`での信頼区間の表を返します。精度パラメータは、表の最後の行に含まれます。

この関数によって返されるオブジェクトは、表形式データのための[Tables.jl](https://github.com/JuliaData/Tables.jl/)インターフェースを実装しています。
