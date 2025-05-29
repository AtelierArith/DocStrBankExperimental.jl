```
function minimum_x(a::Array{T,N}) where T <: AbstractPoint where N
function minimum_x(a::Array{T,N}) where T <: AbstractParticle where N
function minimum_x(a::StructArray)
```

配列 `a` の点の最小 `:x` フィールドを返します 配列 `a` の粒子の最小 `Pos.x` を返します
