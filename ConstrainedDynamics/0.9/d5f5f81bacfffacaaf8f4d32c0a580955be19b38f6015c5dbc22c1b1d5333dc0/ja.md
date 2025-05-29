```julia
mutable struct Body{T} <: ConstrainedDynamics.AbstractBody{T}
```

`Body`は[`Mechanism`](@ref)のコンポーネントです。

# 重要な属性

  * `id`:    ボディの一意のID。`Mechanism`に追加されたときに割り当てられます。
  * `name`:  ボディの名前。名前はURDFから取得されるか、ユーザーによって割り当てられます。
  * `m`:     ボディの質量。
  * `J`:     ボディの慣性。
  * `state`: ボディの状態。すべての位置と速度情報を含みます（[`State`](@ref)を参照）。
  * `shape`: ボディの視覚化形状（[`Shape`](@ref)を参照）。

# コンストラクタ

```
Body(m, J; name, shape)  
Mesh(path, m, J; scale, kwargs...)  
Box(x, y, z, m; kwargs...)  
Cylinder(r, h, m; kwargs...)  
Sphere(r, m; kwargs...)  
Pyramid(w, h, m; kwargs...)
```
