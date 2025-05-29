```
informationmatrix(model::BetaRegressionModel; expected=true)
```

モデルの情報行列を計算します。デフォルトでは、これはフィッシャー情報、すなわち[`params`](@ref)の各要素に関する[`loglikelihood`](@ref)の二次偏導関数の行列の期待値です。`expected`を`false`に設定すると、観測情報を取得できます。

参照: [`vcov`](@ref), [`score`](@ref)
