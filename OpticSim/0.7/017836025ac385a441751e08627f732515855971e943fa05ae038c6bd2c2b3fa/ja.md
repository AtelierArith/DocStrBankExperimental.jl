```
MultiHologramInterface{T} <: OpticalInterface{T}
```

単一の表面上に複数の重なった [`HologramInterface`](@ref) を表すインターフェース。各光線は使用するインターフェースをランダムに選択します。

```julia
MultiHologramInterface(interfaces::Vararg{HologramInterface{T}})
MultiHologramInterface(interfaces::Vector{HologramInterface{T}})
```
