```
Ray{T,N} <: AbstractRay{T,N}
```

Purely geometric ray, defined as `origin + alpha * direction`.

```julia
Ray(origin::SVector{N,T}, direction::SVector{N,T})
```

Has the following accessor methods:

```julia
direction(ray::Ray{T,N}) -> SVector{N,T}
origin(ray::Ray{T,N}) -> SVector{N,T}
```
