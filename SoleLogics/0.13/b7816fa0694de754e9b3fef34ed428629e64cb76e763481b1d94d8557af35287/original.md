```
const AbstractWorlds{W} = AbstractVector{W} where {W<:AbstractWorld}
const Worlds{W} = Vector{W} where {W<:AbstractWorld}
```

Useful aliases for dealing with worlds sets/arrays.

See also [`accessibles`](@ref), [`AbstractWorld`](@ref).
