```
SymmetricAdapter{T} <: Adapter{T, T}
```

抽象アダプタ型。`encode`はシリアル化とデシリアル化の両方に使用されます。

## メソッド

  * [`subcon(adapter::SymmetricAdapter{T})`](@ref subcon)
  * [`encode(adapter::SymmetricAdapter{T}, obj::T; contextkw...)`](@ref encode)
