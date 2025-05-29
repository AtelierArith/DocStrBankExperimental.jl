```
struct Parallelepiped{D, T} <: AbstractRegion{D}
```

平行四辺形/平行六面体である領域

関連情報としては [`Parallelepiped(vecs)`](@ref)、[`Parallelepiped(vecs::T) where {T<:Real}`](@ref) を参照してください。

# フィールド

  * `vecs::Matrix{T}`: 平行四辺形/平行六面体を定義する列ベクトルを持つ行列
  * `vecs_inv::Matrix{T}`: `vecs` の逆行列。
