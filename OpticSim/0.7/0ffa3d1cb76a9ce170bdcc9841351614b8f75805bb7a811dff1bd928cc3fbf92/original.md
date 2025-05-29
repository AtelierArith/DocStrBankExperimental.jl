```
ParametricSurface{T,N} <: Surface{T}
```

`T` is the number type used to represent the surface, e.g., `Float64`. `N` is the dimension of the space the surface is embedded in. `ParametricSurface`s are valid CSG objects, in some cases (where analytic intersection isn't possible) they must be wrapped in an [`AcceleratedParametricSurface`](@ref) for use.

**Must** implement the following:

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
