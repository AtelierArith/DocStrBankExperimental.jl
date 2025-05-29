```
function maximum_y(a::Array{T,N}) where T <: AbstractPoint where N
function maximum_y(a::Array{T,N}) where T <: AbstractParticle where N
function maximum_y(a::StructArray)
```

配列 `a` の点の最大 `:y` フィールドを返します 配列 `a` の粒子の最大 `Pos.y` を返します
