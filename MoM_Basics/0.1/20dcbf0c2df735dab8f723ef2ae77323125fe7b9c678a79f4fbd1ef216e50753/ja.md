```
greenfunc(R::T) where {T<:AbstractFloat}
greenfunc(pa::Vec3D{T}, pb::Vec3D{T}) where {T<:AbstractFloat}
greenfunc(pa::AbstractVector{T}, pb::AbstractVector{T}) where {T<:AbstractFloat}
greenfunc(R::T, k::T) where {T<:AbstractFloat}
greenfunc(pa::Vec3D{T}, pb::Vec3D{T}, k::T) where {T<:AbstractFloat}
```

計算正規化自由空間グリーン関数 $g(R) =  exp^{-1im*K_0*R}/R$
