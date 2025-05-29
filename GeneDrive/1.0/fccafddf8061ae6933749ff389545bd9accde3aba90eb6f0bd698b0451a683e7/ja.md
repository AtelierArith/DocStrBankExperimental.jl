```
mutable struct ConstantTemperature <: Temperature end
```

シミュレーション用のデータで、単一の定常温度（°C）を特徴としています。内部で生成されます。

# 引数

  * `value::Float64`: °Cでの温度値; モデルが各タイムステップで再利用します。
