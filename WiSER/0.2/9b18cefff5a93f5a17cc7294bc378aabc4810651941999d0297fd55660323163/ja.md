```
nlsv_obj!(obs::WSVarLmmObs, β, τ, Lγ, needgrad::Bool) 
nlsv_obj!(m::WSVarLmmModel; needgrad::Bool)
```

与えられたデータとパラメータ値に対して分散推定のための非線形最小二乗（NLS）基準を評価します。`needgrad=true`の場合、勾配が計算されます。`needhess=true`の場合、期待されるヘッセ行列が計算されます。`updateres=true`の場合、まず平均レベルの残差を更新します。`m.iswtnls[1]=true`の場合、重み付き`nlsv_obj!()`関数を評価します。重み付きバージョンの`nlsv_obj!()`を使用する前に、`update_wtmat!(m)`を呼び出して重み行列のコンポーネントを更新する必要があります。
