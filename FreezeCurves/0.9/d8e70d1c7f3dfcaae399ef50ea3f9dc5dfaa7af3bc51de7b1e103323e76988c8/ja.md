```
sfccsolve(obj::SFCCInverseEnthalpyObjective, solver::SFCCNewtonSolver, T₀::Number, ::Val{return_all}=Val{true}(); error_when_not_converged=true)
```

`obj`を専門のニュートン`sovler`を使用して解決し、結果を返します。`return_all`が`true`の場合、名前付きタプル`(;T, Tres, θw, C, itercount)`が返されます。それ以外の場合（デフォルトでは）、温度解のみが返されます。
