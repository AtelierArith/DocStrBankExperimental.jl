```
FCN(cost::CostFunction, grad=true)
```

CostFunctionからJuliaFcnオブジェクトを作成します。

## 引数

  * `fnc::CostFunction` : 最小化するCostFunction。
  * `grad::Bool=true` : `true`の場合、コスト関数の勾配が使用されます。`false`の場合、勾配は使用されません。

## 戻り値

  * `JuliaFcn` : Minuitで使用できる抽象C++クラス`Minuit::FCNBase`から継承されたJuliaFcnオブジェクト。
