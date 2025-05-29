```
function minimum_z(a::Array{T,N}) where T <: AbstractPoint where N
function minimum_z(a::Array{T,N}) where T <: AbstractParticle where N
function minimum_z(a::StructArray)
```

配列 `a` の点の最小 `:z` フィールドを返します 配列 `a` の粒子の最小 `Pos.z` を返します
