```
function maximum_z(a::Array{T,N}) where T <: AbstractPoint where N
function maximum_z(a::Array{T,N}) where T <: AbstractParticle where N
function maximum_z(a::StructArray)
```

配列 `a` の点の最大 `:z` フィールドを返します 配列 `a` の粒子の最大 `Pos.z` を返します
