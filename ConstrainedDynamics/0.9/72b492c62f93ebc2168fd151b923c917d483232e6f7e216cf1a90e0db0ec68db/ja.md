```julia
mutable struct Origin{T} <: ConstrainedDynamics.AbstractBody{T}
```

`Origin`は[`Mechanism`](@ref)のルートです。

# 重要な属性

  * `id`:    オリジンの一意のID。`Mechanism`に追加されたときに割り当てられます。
  * `name`:  オリジンの名前。名前はURDFから取得されるか、ユーザーによって割り当てられます。
  * `shape`: オリジンの視覚化形状（[`Shape`](@ref）を参照）。

# コンストラクタ

```
Origin(; name, shape)  
Origin{Type}(; name, shape)  
Origin(body)
```
