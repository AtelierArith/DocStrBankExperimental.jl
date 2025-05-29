```
struct Parallelepiped{D, T} <: AbstractRegion{D}
```

Region that is a Parallelogram/Parallelepiped

See also [`Parallelepiped(vecs)`](@ref), [`Parallelepiped(vecs::T) where {T<:Real}`](@ref)

# Fields

  * `vecs::Matrix{T}`: Matrix with column vectors defining Parallelogram/Parallelepiped
  * `vecs_inv::Matrix{T}`: Inverse of `vecs`.
