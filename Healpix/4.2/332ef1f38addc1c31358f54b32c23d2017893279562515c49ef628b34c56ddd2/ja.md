```
mutable struct PolarizedHealpixMap{T, O <: Healpix.Order, AA <: AbstractArray{T, 1}}
```

偏光I/Q/Uマップです。3つの同じNSIDEを持つHealpixマップを含みます：

  * `i`
  * `q`
  * `u`

この型のインスタンスは、次の3つのバリエーションの関数[`PolarizedHealpixMap{T,O}`](@ref)を使用して作成できます：

  * `PolarizedHealpixMap(i::HealpixMap{T,O,AA}, q::HealpixMap{T,O,AA}, u::HealpixMap{T,O,AA})`
  * `PolarizedHealpixMap{T,O}(i::AbstractVector{T}, q::AbstractVector{T}, u::AbstractVector{T})`
  * `PolarizedHealpixMap{T,O}(nside::Number)`
