```
const AbstractWorlds{W} = AbstractVector{W} where {W<:AbstractWorld}
const Worlds{W} = Vector{W} where {W<:AbstractWorld}
```

世界のセット/配列を扱うための便利なエイリアスです。

[`accessibles`](@ref)や[`AbstractWorld`](@ref)も参照してください。
