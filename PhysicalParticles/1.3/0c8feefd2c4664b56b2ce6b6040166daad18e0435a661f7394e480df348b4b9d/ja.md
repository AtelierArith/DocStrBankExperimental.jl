```
function maximum_x(a::Array{T,N}) where T <: AbstractPoint where N
function maximum_x(a::Array{T,N}) where T <: AbstractParticle where N
function maximum_x(a::StructArray)
```

配列 `a` の点の最大 `:x` フィールドを返します 配列 `a` の粒子の最大 `Pos.x` を返します
