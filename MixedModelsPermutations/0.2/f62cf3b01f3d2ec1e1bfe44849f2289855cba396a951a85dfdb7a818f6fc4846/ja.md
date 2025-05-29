```
MixedModels.residuals(model::LinearMixedModel, blups)
```

混合モデルの残差を計算しますが、**blupsは無視します**。

これは、[`nonparametricboostrap`](@ref) と [`permutation`](@ref) が常にキーワード引数 `residual_method` が二引数メソッドであると仮定できるようにするための便利な関数です。

!!! warning
    このメソッドは現在、MixedModels.jlから盗用されており、将来のリリースで名前が変更されるか削除される可能性があります。

