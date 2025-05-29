```
Intersection{T,N} <: IntervalPoint{T}
```

Represents the point at which an [`Ray`](@ref) hits a [`Surface`](@ref). This consists of the distance along the ray, the intersection point in world space, the normal in world space, the UV on the surface and the [`OpticalInterface`](@ref) hit.

Has the following accessor methods:

```julia
point(a::Intersection{T,N}) -> SVector{N,T}
normal(a::Intersection{T,N}) -> SVector{N,T}
uv(a::Intersection{T,N}) -> SVector{2,T}
u(a::Intersection{T,N}) -> T
v(a::Intersection{T,N}) -> T
α(a::Intersection{T,N}) -> T
interface(a::Intersection{T,N}) -> OpticalInterface{T}
flippednormal(a::Intersection{T,N}) -> Bool
```
