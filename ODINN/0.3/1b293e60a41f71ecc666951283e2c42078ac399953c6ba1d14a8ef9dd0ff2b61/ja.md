```
DiscreteAdjoint{VJP <: AbstractVJPMethod} <: AbstractAdjointMethod
```

手動でのODEスキームの逆方向実装を伴うSIA2Dの離散随伴。

# フィールド

  * `VJP_method`: 随伴計算内でVJPを計算するために使用されるAbstractVJPMethodの型。
