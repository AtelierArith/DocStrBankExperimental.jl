```
Adapter{TSub, T} <: Wrapper{TSub, T}
```

抽象アダプタ型。

## メソッド

  * [`subcon(adapter::Adapter{TSub, T})`](@ref subcon)
  * [`encode(adapter::Adapter{TSub, T}, obj::T; contextkw...)`](@ref encode)
  * [`decode(adapter::Adapter{TSub, T}, obj::TSub; contextkw...)`](@ref decode)
