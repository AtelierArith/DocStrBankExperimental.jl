```
params(model::BetaRegressionModel)
```

推定されたモデルパラメータのベクトル $\theta = [\beta_1, \ldots, \beta_p, \phi]$ を返します。すなわち、回帰係数と精度です。

!!! danger
    この配列を変更すると、モデルオブジェクトが無効になる可能性があります。


参照: [`coef`](@ref), [`precision`](@ref)
