動的勾配のための静的生成器。

```julia
using QuantumPropagators.Controls: evaluate

G::GradgenOperator = evaluate(gradgen::GradGenerator; vals_dict)
```

は、[`GradGenerator`](@ref)内のすべての制御に特定の値を代入した結果です。

得られたオブジェクトは、[`GradVector`](@ref)と直接乗算することができ、例えば、区分定数時間伝播の評価プロセスで使用されます。
