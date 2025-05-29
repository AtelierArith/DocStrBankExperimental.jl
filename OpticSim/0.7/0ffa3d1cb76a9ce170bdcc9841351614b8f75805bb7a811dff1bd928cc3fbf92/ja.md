```
ParametricSurface{T,N} <: Surface{T}
```

`T` はサーフェスを表すために使用される数値型で、例えば `Float64` です。`N` はサーフェスが埋め込まれている空間の次元です。`ParametricSurface` は有効な CSG オブジェクトであり、場合によっては（解析的交差が不可能な場合）[`AcceleratedParametricSurface`](@ref) にラップする必要があります。

**次のことを実装する必要があります：**

```julia
uv(surface::ParametricSurface{T,N}, p::SVector{N,T}) -> SVector{2,T}
uvrange(surface::ParametricSurface{T,N}) -> Tuple{Tuple{T,T},Tuple{T,T}}
point(surface::ParametricSurface{T,N}, u::T, v::T) -> SVector{N,T}
partials(surface::ParametricSurface{T,N}, u::T, v::T) -> Tuple{SVector{N,T}, SVector{N,T}}
normal(surface::ParametricSurface{T,N}, u::T, v::T) -> SVector{N,T}
inside(surface::ParametricSurface{T,N}, p: :SVector{N,T}) -> Bool
onsurface(surface::ParametricSurface{T,N}, p::SVector{N,T}) -> Bool
surfaceintersection(surface::ParametricSurface{T,N}, AbstractRay::Ray{T,N}) -> Union{EmptyInterval{T},Interval{T},DisjointUnion{T}}
interface(surface::ParametricSurface{T,N}) -> OpticalInterface{T}
```
