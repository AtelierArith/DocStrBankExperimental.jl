```
greenfunc(R::T) where {T<:AbstractFloat}
greenfunc(pa::Vec3D{T}, pb::Vec3D{T}) where {T<:AbstractFloat}
greenfunc(pa::AbstractVector{T}, pb::AbstractVector{T}) where {T<:AbstractFloat}
greenfunc(R::T, k::T) where {T<:AbstractFloat}
greenfunc(pa::Vec3D{T}, pb::Vec3D{T}, k::T) where {T<:AbstractFloat}
```

计算归一化自由空间格林函数 $g(R) =  exp^{-1im*K_0*R}/R$
