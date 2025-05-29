```
function minimum_y(a::Array{T,N}) where T <: AbstractPoint where N
function minimum_y(a::Array{T,N}) where T <: AbstractParticle where N
function minimum_y(a::StructArray)
```

配列 `a` の点の最小 `:y` フィールドを返します 配列 `a` の粒子の最小 `Pos.y` を返します
